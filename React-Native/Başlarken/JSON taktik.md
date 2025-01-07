const [selectedImage, setSelectedImage] = useState<string | null>(null);

  const [paintingName, setPaintingName] = useState("");

  const [paintingYear, setPaintingYear] = useState("");

  const [paintingArtist, setPaintingArtist] = useState("");

  const [paintingMovement, setPaintingMovement] = useState("");

  const [paintingPlace, setPaintingPlace] = useState("");

  

  const user = {

    selectedImage,

    paintingName,

    paintingYear,

    paintingArtist,

    paintingMovement,

    paintingPlace

  }
  
  
  
  burada selected image isimli nesne selectedImage olarak içindekini döndürür.
  Yani mesela navigate ile selectedImage nesnesini yollayacağız . 
  
  navigat( {selectedImage: selectedImage }) yapmamıza gerek yok aynı ad olduğu içim