<h1>HW1</h1>
    
```swift

import SwiftUI


struct TitleView: View {
    var body: some View {
        VStack (alignment:.center,spacing:2){
            Text("1103308的冰箱")
                .foregroundColor(Color(red:20/225,green:40/255,blue:255/255))
                .font(.system(size:30))
                .fontWidth(.expanded)
                .fontWeight(.bold)
        }
    }
}
struct ContentView:View{
    var body:some View{
        
        VStack{
            TitleView()
            HStack{
                Image ("Turkey")
                    .resizable()
                    .frame(width:200,height:120,alignment:.center)
                    .offset(y:40)
                Image ("Milk")
                    .resizable()
                    .frame(width:80,height:120,alignment:.center)
                    .offset(y:25)
            }
            HStack{
            
                Image ("Cola")
                    .resizable()
                    .frame(width:100,height:120,alignment:.center)
                    .offset(x:140,y:25)
                Image ("Sprite")
                    .resizable()
                    .frame(width:120,height:96,alignment:.center)
                    .offset(x:60,y:25)
                Image("Water")
                    .resizable()
                    .frame(width:80,height:120,alignment:.center)
                    .offset(x:-10,y:20)
                Image("Water")
                    .resizable()
                    .frame(width:80,height:120,alignment:.center)
                    .offset(x:-60,y:20)
                Image("Water")
                    .resizable()
                    .frame(width:80,height:120,alignment:.center)
                    .offset(x:-110,y:20)
            }
            HStack{
                
                Image ("Jack")
                    .resizable()
                    .frame(width:270,height:170)
                    .offset(x:10,y:10)
                Image ("Jar")
                    .resizable()
                    .frame(width:130,height:150,alignment:.center)
                    .offset(x:-60,y:10)
            }
            HStack{
                VStack{
                    Image ("Meat")
                        .resizable()
                        .frame(width:100,height:120,alignment:.center)
                        .offset(x:10,y:25)
                        .overlay(
                            Image ("Meat")
                                .resizable()
                                .frame(width:100,height:120,alignment:.center)
                                .offset(x:15,y:10)
                                .overlay(
                                Image ("Meat")
                                    .resizable()
                                    .frame(width:100,height:120,alignment:.center)
                                    .offset(x:20,y:-5)
                            )
                        )
                }
                Image ("Cheese")
                    .resizable()
                    .frame(width:150,height:120,alignment:.center)
                    .offset(y:15)
            }
        }
        .background(
            Image("Fridge1")
                .resizable()
                .frame(width:400,height:800)
        )
    }
}


extension UIScreen{
    static let screenWidth=UIScreen.main.bounds.size.width
    static let screenHeight=UIScreen.main.bounds.size.height
    static let screenSize=UIScreen.main.bounds.size
}







    
```

<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW3.png">
