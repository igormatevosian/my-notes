#python #db #tools 
![[logo-margin-white-vector.svg|500]]
## Тестирование с in-memory db
```python
from fastapi.testclient import TestClient
from sqlmodel import Session, SQLModel, create_engine
from sqlmodel.pool import StaticPool  
from .main import app, get_session

@pytest.fixture(name="session")  
def session_fixture():  
    engine = create_engine(
        "sqlite://", connect_args={"check_same_thread": False}, poolclass=StaticPool
    )
    SQLModel.metadata.create_all(engine)
    with Session(engine) as session:
        yield session
```

