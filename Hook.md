
const fetchGroups = async () => {  
  const response = await axiosNoToken.get(`groups`);  
  if (response.data.type === 'SUCCESS') {  
    setDepartmentGroups(response.data.data);  
  } else {  
    console.error('Failed to fetch groups');  
  }  
};  
  
const [loading, sendRequest] = useRequestLoadingState({  
  request: fetchGroups,  
  onError: (error) => console.error('Error fetching groups:', error),  
});  
  
useEffect(() => {  
  sendRequest();  
}, []);