import SwiftUI

struct ContentView: View {
    var body: some View {
        VStack {
            Text("1103308          詹旻嘉")
                .fontWeight(.heavy)
                .font(.system(size:38))
                .foregroundColor(Color(red:100/255,green:70/255,blue:215/255))
            Image("Chan2")
                .resizable()
                .scaledToFit()
                .foregroundColor(.white)
                .shadow(color: .gray, radius: 3, x: 0.5, y: 0.5)
            Text("我直接在作業1跳舞 ")
                .padding(.all,10)
                .fontWeight(.semibold)
                .frame(width:380, height:230, alignment:.top)
                .font(.system(size:41))
                .background(Color(red:135/255,green:100/255,blue:225/255))
                .foregroundColor(Color(red:0/255,green:180/255,blue:255/255))
                .border(Color(red:139/255,green:120/255,blue:255/255),width:3)
                .cornerRadius(10)
                .overlay(
                    Text("ጿ ኈ ቼ ኈ ዽ ቼ ጿ ዽ ኈ ቼ ኈ           ጿ ኈ ቼ ኈ ዽ ቼ           ኈ ቼ ኈ ")
                        .padding(.all,10)
                        .fontWeight(.semibold)
                        .font(.system(size:41))
                        .offset(x:0,y:20)
                        .foregroundColor(Color(red:20/255,green:220/255,blue:225/255))
                )
                .overlay(
                    Image(systemName: "figure.dance")
                        .font(.system(size:80,weight:.light))
                        .foregroundColor(Color(red:20/255,green:200/255,blue:255/255))
                        .offset(x:0,y:45)
                )
        }
        .background(Color(red:180/255,green:153/255,blue:255/255))
    }
}
;
struct ContentView_Preiviews: PreviewProvider
{
    static var previews: some View 
    {
        ContentView()
    }
}
