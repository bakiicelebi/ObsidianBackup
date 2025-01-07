https://github.com/facebook/react-native/issues/31697#issuecomment-1150831275

![[Pasted image 20240524004309.png]]



### !  çözmedi :

useEffect(()=>{

    LogBox.ignoreLogs([

      'VirtualizedLists should never be nested inside plain',

    ]);

  },[])
