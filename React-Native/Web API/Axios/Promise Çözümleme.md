//Çıktıları kontrol et async await ve normal fonksiyonları

  

    async function handleRequest() {

        console.log("1")

        await axios

            .get('https://jsonplaceholder.typicode.com/users/2')

        console.log("3")

    }

    // function handleRequest(){

    //     console.log("1")

    //     axios

    //         .get('https://jsonplaceholder.typicode.com/users/2')

    //         .then(response => console.log("2"))

    //         .catch(error => console.log(error))  //olumlu cevap varsa then,  olumsuz cevap varsa catch()

    //         console.log("3")

    // }

  

    /* HATAYI TRY CATCH İLE YAKALAMA */

    // async function handleRequest() {

    //     try {

    //         await axios

    //             .get('https://jsonplaceholder.typicode.com/users/2')

    //         console.log("3")

  

    //     } catch (error) {

    //         console.log(error)

    //     }

    // }


isteğin gelmesini bekleyip isteği döndürürsen async await diğer türlü isteğin gelmesini beklemeden; istek geldiğinde kendi dönsün istersen then catch

![[Pasted image 20240218230121.png]]