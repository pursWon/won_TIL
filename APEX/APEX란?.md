APEX란?
=========================

**APEX**는 객체지향언어로 Lightning Platform에서 저장되고, 컴파일되며, 실행된다.   

Data 타입의 모든 변수는 기본적으로 null로 초기화된다.   

- Integer
- Double
- Long
- Date
- Datetime
- String
- Boolean
- ID

Collection 타입은 List, Set, Map을 사용한다.   

</br>

**(1) List**



```Apex

List<String> myStrings = new List<String>();

String[] myStrings = new List<String>;

myStrings.add('Strings1');
myStrings.add('Strings2');

```

</br>

데이터베이스의 SQL과 Query를 주고 받을 때는, List를 주로 사용한다.   

```Apex

List<Account> myAccounts = [SELECT Id, Name FROM Account];

```

</br>

인덱스는 0부터 시작.

```Apex

List<Account> myAccounts = [SELECT Id, Name FROM Account];
String firstAccount = myAccounts[0].Name;

```

</br></br>

**(2) Set**

중복을 허용하지 않는 유형의 Collection Type.      

ID 값은 항상 고유한 값이므로, ID값을 저장할 때 Set를 사용한다.    

다음과 같이 SQL Query에서의 WHERE 절의 일부로 사용할 수 있다.    

```Apex

Set<ID> accountIds = new Set<ID>{ '001123123123AA2', '001DA44444DD'};
List<Account> accounts = [SELECT Name FROM Account WHERE Id IN :accountIds];

```

</br></br>

**(3) Map** 

Key, Value 쌍의 모음

Swift에선 Dictionary가 이 역할이었는데, APEX에선 Map이 담당한다.    

```Apex

Map<Id, Account> accountMap = new Map<Id, Account>([SELECT Id, Name FROM Account]);

```

</br>

get(Key) : Map에 저장된 Key에 해당되는 Value를 가져온다.   

```Apex

Id accId = '001d000000boasdSAA2';

Account account = accountMap.get(accId);

```

</br>

put(Key, Value) : Map의 Key에 해당하는 value를 저장한다.

```Apex

Account acct = new Account();
acct.Id = '001d000000boasdSAA2';
acct.Name = '삽입될 계정이름';

Map<Id, Account> accountMap = new Map<Id, Account>();
accountMap.put(acct.Id, acct);

```













