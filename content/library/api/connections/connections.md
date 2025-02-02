---
title: Connections and databases
slug: /library/api-reference/connections
---

# Connections and databases

## Setup your connection

<TileContainer>
<RefCard href="/library/api-reference/connections/st.connection" size="half">

<Image pure alt="screenshot" src="/images/api/connection.svg" />

#### Create a connection

Connect to a data source or API

```python
conn = st.connection('pets_db', type='sql')
pet_owners = conn.query('select * from pet_owners')
st.dataframe(pet_owners)
```

</RefCard>
</TileContainer>

## Built-in connections

<TileContainer>

<RefCard href="/library/api-reference/connections/st.connections.snowflakeconnection" size="half">

<Image pure alt="screenshot" src="/images/api/connections.SnowflakeConnection.svg" />

#### SnowflakeConnection

A connection to Snowflake.

```python
conn = st.connection('snowflake')
```

</RefCard>

<RefCard href="/library/api-reference/connections/st.connections.sqlconnection" size="half">

<Image pure alt="screenshot" src="/images/api/connections.SQLConnection.svg" />

#### SQLConnection

A connection to a SQL database using SQLAlchemy.

```python
conn = st.connection('sql')
```

</RefCard>
</TileContainer>

## Third-party connections

<TileContainer>
<RefCard href="/library/api-reference/connections/st.connections.baseconnection" size="half">

#### Connection base class

Build your own connection with `BaseConnection`.

```python
class MyConnection(BaseConnection[myconn.MyConnection]):
    def _connect(self, **kwargs) -> MyConnection:
        return myconn.connect(**self._secrets, **kwargs)
    def query(self, query):
        return self._instance.query(query)
```

</RefCard>

</TileContainer>
