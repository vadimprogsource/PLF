```csharp
ArrayBuilder
{
      m_capacity;

     ArrayBuilder(cap)=>m_capacity = cap;

    Capacity=>m_capacity;

       BuildArray(len)
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


{
       ArrayBuilder builder = StringArrayBuilder();
       array = bulder.BuildArray(100);
       (item;array[1..]) >>item;
       ~array();
      ~builder();
}
```
