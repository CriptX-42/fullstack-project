---
Created: 2025-05-06
---
---
Suponhamos que temos um serviço que depende de um `HttpClient` e de um `LoggerService`

```typescript
@Injectable({
  providedIn: 'root',
})
export class UserService {
  constructor(private http: HttpClient, private logger: LoggerService) {}

  getUser(id: number): Observable<User> {
    this.logger.log(`Getting user with id ${id}`);
    return this.http.get<User>(`/api/users/${id}`);
  }
}

```


O Teste do serviço ficaria assim:

```typescript
describe('UserService', () => {
  let service: UserService;
  let httpMock: HttpTestingController;
  let loggerSpy: jasmine.SpyObj<LoggerService>;

  beforeEach(() => {
    const spy = jasmine.createSpyObj('LoggerService', ['log']);

    TestBed.configureTestingModule({
      imports: [HttpClientTestingModule],
      providers: [
        UserService,
        { provide: LoggerService, useValue: spy }
      ]
    });

    service = TestBed.inject(UserService);
    httpMock = TestBed.inject(HttpTestingController);
    loggerSpy = TestBed.inject(LoggerService) as jasmine.SpyObj<LoggerService>;
  });

  afterEach(() => {
    httpMock.verify(); // Verifica que não há requisições pendentes
  });

  it('should fetch user and log the request', () => {
    const mockUser: User = { id: 1, name: 'João' };

    service.getUser(1).subscribe(user => {
      expect(user).toEqual(mockUser);
    });

    const req = httpMock.expectOne('/api/users/1');
    expect(req.request.method).toBe('GET');
    req.flush(mockUser);

    expect(loggerSpy.log).toHaveBeenCalledWith('Getting user with id 1');
  });
});

```


> [!NOTE] Algumas informações
> - `HttpClientTestingModule`  é usado para mockar as requisições HTTP
> - **Espione serviços com `jasmine.createSpyObj`**: Para controlar o comportamento de serviços auxiliares.

