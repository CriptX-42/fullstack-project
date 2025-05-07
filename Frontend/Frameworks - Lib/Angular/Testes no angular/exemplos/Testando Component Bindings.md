---
Created: 2025-05-06
---
----
#### Componente filho

```typescript
@Component({
  selector: 'app-child',
  template: `<button (click)="notify()">Notify</button>`,
})
export class ChildComponent {
  @Input() message!: string;
  @Output() notified = new EventEmitter<string>();

  notify() {
    this.notified.emit(this.message);
  }
}

```

#### Componente pai
```typescript
@Component({
  template: `<app-child [message]="msg" (notified)="onNotified($event)"></app-child>`
})
class HostComponent {
  msg = 'Hello';
  receivedMessage = '';

  onNotified(message: string) {
    this.receivedMessage = message;
  }
}

```


```typescript
describe('ChildComponent bindings', () => {
  let hostFixture: ComponentFixture<HostComponent>;

  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [ChildComponent, HostComponent]
    });

    hostFixture = TestBed.createComponent(HostComponent);
    hostFixture.detectChanges();
  });

  it('should bind input message and emit output correctly', () => {
    const button = hostFixture.nativeElement.querySelector('button');
    button.click();

    hostFixture.detectChanges();
    const hostInstance = hostFixture.componentInstance;

    expect(hostInstance.receivedMessage).toBe('Hello');
  });
});

```