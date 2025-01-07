////

**const { data, error, loading } = UseFetch(API_CATEGORIES);
  const renderData = ({ item }: any) => <CategoryCard data={item} />
<FlatList numColumns={2} data={data} renderItem={renderData} keyExtractor={(item:any) => item.idCategory} />

////

