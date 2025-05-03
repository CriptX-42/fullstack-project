---
Created: 2025-05-02
---
-----
- Como nossa lib é bem completa, o angular oferece o `HttpClientModule` para nos facilitar na comunicação e requisição `HTTP`, nos ajuda com `GET`, `POST`, `PUT`, `DELETE` e entre outras.

Importando módulo HTTP no nosso projeto

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { HttpClientModule } from '@angular/common/http';  // Importando HttpClientModule

import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, HttpClientModule],  // Adicionando o HttpClientModule
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule {}

```


### Criando um serviço HTTP

```
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

@Injectable({
  providedIn: 'root'
})
export class ApiService {

  private apiUrl = 'https://api.exemplo.com/';

  constructor(private http: HttpClient) {}

  // Método GET
  getData(): Observable<any> {
    return this.http.get(`${this.apiUrl}data`);
  }

  // Método POST
  sendData(data: any): Observable<any> {
    return this.http.post(`${this.apiUrl}data`, data);
  }

  // Método PUT
  updateData(id: number, data: any): Observable<any> {
    return this.http.put(`${this.apiUrl}data/${id}`, data);
  }

  // Método DELETE
  deleteData(id: number): Observable<any> {
    return this.http.delete(`${this.apiUrl}data/${id}`);
  }
}

```

#### Usando esse mesmo serviço

```
import { Component, OnInit } from '@angular/core';
import { ApiService } from './api.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  data: any;

  constructor(private apiService: ApiService) {}

  ngOnInit(): void {
    // Chamando o método GET
    this.apiService.getData().subscribe(
      (response) => {
        this.data = response;
        console.log(this.data);
      },
      (error) => {
        console.error('Erro ao buscar dados', error);
      }
    );
  }
}

```


-----
### Tratamento de erros

Da também para tratarmos os erros na requisição `HTTP` retornando o `Observable`. Usamos o operador `catchError` para tal


```
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable, throwError } from 'rxjs';
import { catchError } from 'rxjs/operators';

@Injectable({
  providedIn: 'root'
})
export class ApiService {
  private apiUrl = 'https://api.exemplo.com/';

  constructor(private http: HttpClient) {}

  getData(): Observable<any> {
    return this.http.get(`${this.apiUrl}data`).pipe(
      catchError((error) => {
        console.error('Erro ao obter dados', error);
        return throwError(() => new Error('Erro ao obter dados'));
      })
    );
  }
}

```