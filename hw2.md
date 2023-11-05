<h1>HW2</h1>
    
```swift

     import SwiftUI


struct ContentView: View {
    @State var count:Int=4
    @State var result:Bool=false
    @State var lose:Bool=false
    @State var tie:Bool=false
    @State var alertTypes:Game? = nil
    
    enum Game{
        case tie
        case loss
        case victory
    }
    var body: some View 
    {
        VStack{
            if(count==0)
            {
                Image("Paper")
                    
                    .padding(.all,10)
                    .frame(width:400, height:450,alignment:.bottom)
                    .rotationEffect(.degrees(180))
            }
            else if(count==1)
            {
                Image("Scissors")
                    .padding(.all,10)
                    .frame(width:400, height:450,alignment:.center)
                    .rotationEffect(.degrees(180))
                    
            }
            else if(count==2)
            {
                Image("Stone")
                    .padding(.all,10)
                    .frame(width:400, height:450,alignment:.center)
                    .rotationEffect(.degrees(180))
                
            }
            else if (count==4)
            {
                Image("RockPaperScissors")    
                    .resizable()
                    .padding(.all,10)
                    .frame(width:420,height:450,alignment:.center)
                
            }
            HStack{
                Button(action:{
                    count = Int.random(in:0...2)
                    result.toggle()
                    if (count==0){alertTypes = .tie}
                    else if(count==1){alertTypes = .loss}
                    else if(count==2){alertTypes = .victory}
                }
                       ,
                       label:{
                    Image("Paper")
                        .resizable()
                        .padding(.all,10)
                        .frame(width:125, height:150,alignment: .center)
                        .alert(isPresented:$result, content: {Result()})
                    
                })
                Button(action:{
                    count = Int.random(in:0...2)
                    result.toggle()
                    if (count==0){alertTypes = .loss}
                    else if(count==1){alertTypes = .victory}
                    else if(count==2){alertTypes = .tie}
                }
                       ,
                       label:{
                    Image("Stone")
                        .resizable()
                        .padding(.all,10)
                        .frame(width:125, height:150,alignment: .center)
                        .alert(isPresented:$result, content: {Result()})
                    
                })
                Button(action:{
                    count = Int.random(in:0...2)
                    result.toggle()
                    if (count==0){alertTypes = .victory}
                    else if(count==1){alertTypes = .tie}
                    else if(count==2){alertTypes = .loss}
                }
                    ,
                   label:{
                        Image("Scissors")
                            .resizable()
                            .padding(.all,10)
                            .frame(width:125, height:150,alignment: .center)
                            .alert(isPresented:$result, content: {Result()})
                            
                })
            }
            
        }
        .background(Color.black)
    }
    func Result()->Alert{
        switch alertTypes {
        case .victory:
            return Alert(
                title:Text("You Win!!"),
                dismissButton: .default(Text("OK"),action:{count=4})
            )
        case .tie:
            return Alert(
                title:Text("Tie!!"),
                dismissButton: .default(Text("OK"),action:{count=4})
            )
        case .loss:
            return Alert(
                title:Text("You Lose!!"),
                dismissButton: .default(Text("OK"),action:{count=4})
            )
        default: return Alert(title:Text("error"))
        }
        
    }
}

```

<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW2-1.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW2-2.png">
