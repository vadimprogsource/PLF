```csharp

ArrayList : List
{
    ArrayList(capacity)=>List(capacity);
    Add(item)
    {
      List::Add(item);
      =>; 
    }
    AddRange([] array, fromIndex=0)
    {
         (item;array[fromIndex..]) List::Add(item);
         =>;
    }


    +(item)=>list.Add(item);
    +([] array)=>list.AddRange(array);

    ~ArrayList()=>~List();
}

ArrayBuilder
{
      m_capacity;

     ArrayBuilder(capacity)=>m_capacity = capacity;

    Capacity=>m_capacity;

       [] BuildArray(len)
       {
               array = [len];
              (i=0;i<len;i++) array[i] = BuildItem(i);
              =>array;
       }

      BuildItem(index)=>index;

    ~ArrayBulder()
     {
         ~m_capacity();
     }
}

StringArrayBuilder : ArrayBuilder
{
    StringArrayBuilder(capacity)=>ArrayBuilder(capacity);
    BuildItem(index)=>$»Item NO {index}»;
    ~StringArrayBuilder()=>~ArrayBuilder();
}

Customer
{
   id;
   type;
   name;
}

CrmDataSet : DataSet
{
    CrmDataSet(connectionStr)=>DataSet(connectionStr);
}

{
       ArrayBuilder builder = StringArrayBuilder();
       array = ArrayList().AddRange(builder.BuildArray(100));
       ~builder();
       array += 10000;
       (item;array.Add(1000)[1..][x=>x>5]) >>item;


       crm= CrmDataSet("server=127.1.1.1;database=crm");

       [] list = crm<Customer>[x=>x.type=="org" && x.id>0][..1000]; // select top 1000 * from  customers where type="org" and id>0
       ~crm();
       ~array();
       ~list();
     
}
```
