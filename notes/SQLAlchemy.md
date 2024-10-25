
```python
from sqlalchemy import create_engine, Column, Integer, String
2from sqlalchemy.ext.declarative import declarative_base
3from sqlalchemy.orm import sessionmaker
4
5Base = declarative_base()
6
7class User(Base):
8    __tablename__ = 'users'
9    id = Column(Integer, primary_key=True)
10    name = Column(String)
11
12# Создание engine и сессии
13engine = create_engine('sqlite:///:memory:')  # Используем SQLite в памяти
14Base.metadata.create_all(engine)
15Session = sessionmaker(bind=engine)
16session = Session()
```

