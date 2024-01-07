<h1>HW4</h1>
    
```swift

import SwiftUI

@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}

var courses = [ 
    Course(name:"Temu",image:"Temu",description:"電商購物平台",isFeature: true),
    Course(name:"CapCut",image:"CapCut",description:"影音剪輯軟體",isFeature: true),
    Course(name:"Max",image:"HBOmax",description:"電視電影串流媒體",isFeature: true),
    Course(name:"Threads",image:"Threads",description:"文字版instagram",isFeature: true),
    Course(name:"TikTok",image:"TikTok",description:"短影音平台",isFeature: true),
    Course(name:"Instagram",image:"Instagram",description:"社群平台",isFeature: true),
    Course(name:"Chrome",image:"Chrome",description:"搜尋引擎",isFeature: true),
    Course(name:"YouTube",image:"YouTube",description:"影片串流平台",isFeature: true),
    Course(name:"WhatsApp",image:"WhatsApp",description:"跨平台加密通訊應用程式",isFeature: true),
    Course(name:"Gmail",image:"Gmail",description:"Google郵件",isFeature: true)
]    

var myDictionary = [
    TermAndDescription(term: "Temu", description: "由中國電商巨頭拼多多推出、進軍歐美市場的電商App"),
    TermAndDescription(term: "CapCut", description: "是由字節跳動旗下臉萌科技開發的一款免費的全功能專業影片編輯與製作軟體"),
    TermAndDescription(term: "HBOmax", description: "華納兄弟探索提供的串流媒體影片服務平台"),
    TermAndDescription(term: "Threads", description: "Meta 旗下的社群網路平台。使用者可以在平台上發表相片及文字貼文。"),
    TermAndDescription(term: "TikTok", description: "由中國大陸字節跳動公司所創辦營運的短影片社交平台"),
    TermAndDescription(term: "Instagram", description: "Meta公司的一款免費提供線上圖片及影片分享的社群應用軟體"),
    TermAndDescription(term: "Chrome", description: "Google開發的免費網頁瀏覽器"),
    TermAndDescription(term: "YouTube", description: "美國Alphabet旗下的影片分享網站，也是目前全球最大的影片搜尋和分享平台"),
    TermAndDescription(term: "WhatsApp", description: "Meta 公司旗下一款用於智慧型手機的跨平台加密即時通訊應用程式"),
    TermAndDescription(term: "Gmail", description: "Google公司發布的一個免費電子郵件服務")
    ]

struct ContentView: View {
    var body: some View {
        VStack {
            Text("    2023 \n 熱門APP")
                .font(.largeTitle)
                .fontWeight(.heavy)
                .foregroundStyle(.primary)
            TabView{
                Group{
                    WelcomeView()
                        .tabItem{
                            Image(systemName:"rosette")
                            Text("Welcome")
                        }
                    CourseListView()
                        .tabItem{
                            Image(systemName: "list.dash")
                            Text("Courses")
                        }
                    CardView()
                        .tabItem{
                            Image(systemName: "book")
                            Text("Learn")
                        }
                    SettingView()
                        .tabItem{
                            Image(systemName:"wrench")
                            Text("Setting")
                        }
                }
                .toolbarBackground(Color.gray,for: .tabBar)
                .toolbarBackground(.visible, for: .tabBar)
                .toolbarColorScheme(.light, for: .tabBar)
            }
            .tint(.yellow)
        }
    }
}

struct WelcomeView: View {
    @AppStorage ("UserName") var UserName:String=""
    var body: some View {
    VStack{
        Image("AppIcon")
            .resizable()
            .frame(width:350,height: 280)
            .cornerRadius(20.0)  
        Text("2023\n前十下載的熱門APP")
            .fontWeight(.heavy)
            .lineSpacing(20)
            .font(.system(size: 32.0))
            .foregroundColor(.white)
            .frame(width: 350, height: 150, alignment: .center) .background(Color.blue)
            .cornerRadius(20.0) 
            .multilineTextAlignment(.center)
        }
    } 
}


struct Course:Identifiable
{
    var id = UUID()
    var name:String
    var image:String
    var description:String
    var isFeature:Bool
}
                                              
struct FullImageRow: View { 
    var thisCourse:Course
    var body: some View {
        ZStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width: 350,height: 350) 
                .aspectRatio(contentMode:.fit)
                .cornerRadius(10)
                .overlay(
                    Rectangle()
                        .foregroundColor(.black)
                        .cornerRadius(10)
                        .opacity(0.2))
            Text(thisCourse.name)
                .font(.system(.title))
                .fontWeight(.black)
                .foregroundColor(.white)
                .offset(x:-100.0,y:-150.0)
        }
    } 
}

struct BasicImageRow: View { 
    var thisCourse:Course
    var body: some View {
        HStack{
            Image(thisCourse.image)
                .resizable()
                .frame(width: 40, height: 40) 
                .cornerRadius(5)
            Text(thisCourse.name)
                
        }
    } 
}

struct CourseDetailView:View{
    @Environment(\.presentationMode) 
    var presentationMode 
    var thisCourse:Course
    var body: some View{
        ScrollView{ 
            VStack{
                Image(thisCourse.image) .resizable()
                    .aspectRatio(contentMode: .fill)
                    .clipped()
                Text(thisCourse.name)
                    .font(.system(.title, design:.rounded))
                    .fontWeight(.black)
                Spacer()
                Text(thisCourse.description)
                    .font(.system(.subheadline,design:.rounded))
                    .fontWeight(.light)
                Spacer()
            }
        }
        .overlay(
            HStack{
                Spacer() 
                VStack{
                    Button(action:{
                    
                        self.presentationMode.wrappedValue.dismiss()
                        
                    },label:{ Image(systemName:"chevron.down.circle.fill")
                            .font(.largeTitle) 
                            .foregroundColor(.white)
                    })
                    .padding(.trailing, 20)    
                    .padding(.top, 40) 
                    Spacer()
                }
            }
        )
    }
}

struct CourseListView:View{
    @State var showDetailView=false
    @State var selectedCourse:Course?
    var body: some View{
        NavigationView{
            List(courses){ courseItem in
                if courseItem.isFeature{
                    FullImageRow(thisCourse:courseItem)
                        .onTapGesture{
                            self.showDetailView=true
                            self.selectedCourse=courseItem
                        }
                }else
                    {
                    BasicImageRow(thisCourse: courseItem) .onTapGesture {
                        self.showDetailView = true
                        self.selectedCourse = courseItem }
                }
                
            }
            .sheet(item: self.$selectedCourse){ thisCourse in
                CourseDetailView(thisCourse: thisCourse) }
            .navigationBarTitle("App") 
        }
    }
}

struct TermAndDescription: Identifiable{ 
    var id = UUID()
    var term:String
    var description:String }
        
struct CardView: View {
    @State var currentCard = 0 
    var body: some View {
        VStack{
            VStack{
                Image(myDictionary[currentCard].term)
                    .resizable()
                    .frame(width: 160,height: 160) 
                    .aspectRatio(contentMode:.fit)
                    .cornerRadius(10)
                    .overlay(
                        Rectangle()
                            .foregroundColor(.black)
                            .cornerRadius(10)
                            .opacity(0.2))
                Text(myDictionary[currentCard].term) 
                    .font(.largeTitle)
                    .foregroundColor(.black)
                    .padding(.all, 10) 
                Text(myDictionary[currentCard].description)
                    .font(.body) 
                    .foregroundColor(.blue) 
                    .padding(.all, 10)
            }
            .frame(minWidth: 0, idealWidth: 120, maxWidth: 320,
                   minHeight: 0, idealHeight: 120, maxHeight: 320, alignment: .center) 
            .background(Color.yellow)
            .cornerRadius(30)
            .onTapGesture {
                if currentCard<myDictionary.count-1{
                    currentCard+=1 }
                else{
                    currentCard=0 }
            }
            Text("點擊查看下一張")
                .padding(.all,10)
        }
    }
}

struct SettingView: View {
    let displayFontType=[".default",".rounded",".monospaced",".serief"]
    @State var displayFontSelected=0
    @State var IsDeepScheme=false
    @State var colorArray:Array=[255.0,255.0,255.0]
    @State var stepperValue=0
    @State var sliderValue=0.0
    @State var date=Date()
    var body: some View {
        NavigationView{
            Form(content: {
                Section(header:Text("字型設定"),content:{
                    Picker(selection:$displayFontSelected,
                           label: Text("字型選擇(\(displayFontSelected))"),
                           content:{
                        ForEach(0..<displayFontType.count,id:\.self,content:{Text(self.displayFontType[$0])})
                    })
                })
                Section(header:Text("背景風格"),
                        content:{
                    Toggle(isOn:$IsDeepScheme,
                           label:{Text("深色(\(String(IsDeepScheme)))")})
                })
                Section(header:Text("計數器")){
                    Stepper("Stepper(\(stepperValue))",onIncrement:{stepperValue+=1},onDecrement:{stepperValue-=1})
                }
                Section(header:Text("滑桿(\(sliderValue,specifier:"%.2f"))")){
                    Slider(value:$sliderValue, in:0...1)
                }
                Section(header:DatePicker("日期:",selection:$date)){
                    Text(date.formatted(.dateTime))
                }
            })
            .navigationBarTitle("Settings 設定")
        }
    }
}


    
```

<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-1.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-2.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-3.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-4.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-5.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-6.png">
<img width="40%"  src="https://github.com/RichHakka/Yzu-SwiftUI-1103308/blob/main/HW4-7.png">
