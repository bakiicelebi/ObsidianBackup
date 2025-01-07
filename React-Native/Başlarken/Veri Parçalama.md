
{data} şeklinde gelen verinin data objesini alıyorum

{data: pData} yaparsam data objesini pData adlı değişkene atamış olurum

const fetchData = async () => {

    const { data: productData } = await axios.get(API_URL);

    setData(productData);

  }