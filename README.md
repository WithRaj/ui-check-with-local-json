import 'dart:convert';
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';

class api extends StatefulWidget {
  const api({Key? key}) : super(key: key);

  @override
  _apiState createState() => _apiState();
}

class _apiState extends State<api> {
  @override
  Widget build(BuildContext context) {
    show(String t1,String img)
    {
      return Expanded(
        flex: 1,
        child: Column(
          children: [
            Container(
              child: InkWell(
                  child: Container(
                    //margin: EdgeInsets.only( top: 7,left: 45),
                    height: 60,
                    width: 60,

                    child: Card(
                      shape: RoundedRectangleBorder(
                        borderRadius: BorderRadius.circular(16.0),
                      ),
                      color: Colors.white,
                      elevation: 5,
                      child:Container(
                        padding: EdgeInsets.all(0),
                        decoration: BoxDecoration(
                          shape: BoxShape.circle,
                        ),
                        child:Center(
                          child:  Image.asset(img,height: 40.0
                            ,width: 40.0,),
                        ),
                      ),

                    ),
                  ),
                  onTap: () {
                    ScaffoldMessenger.of(context).showSnackBar(SnackBar(
                        content: Text("$t1")));
                  }),

            ),
            Container(
              margin: EdgeInsets.only(top:1),
              child:  Text(
                t1,textAlign: TextAlign.center,
                style: TextStyle(
                    fontSize: 15,
                    color: Colors.white),
              ),
            ),
          ],
        ),
      );
    }
    return Scaffold(
      body: FutureBuilder(
        future: DefaultAssetBundle.of(context).loadString('asset/first.json'),
        builder: (context, snapshot) {
          var mydata = json.decode(snapshot.data.toString());
          if(mydata==null)
            {
              return Container(
                child: Center(child: Text("Please Wait",style:TextStyle(
                  fontSize: 30,
                ),)),
              );
            }
         else return Scaffold(
            body: Container(
                constraints: BoxConstraints.expand(),
                decoration: BoxDecoration(
                  image: DecorationImage(
                    image: AssetImage('image/bg.jpg'),
                    fit: BoxFit.fill,
                  ),
                ),
                child: ListView(
                  children:<Widget>[ Column(
                    children: [
                      Stack(
                        children: <Widget>[
                          Row(
                            children: <Widget>[
                              InkWell(child:
                              Container(
                                    margin: EdgeInsets.only(left: 40, top: 20),
                                    height: 80,
                                    width: 80,
                                    child: Card(
                                      shape: RoundedRectangleBorder(
                                        borderRadius: BorderRadius.circular(20.0),
                                      ),
                                      color: Colors.white,
                                      elevation: 5,
                                      child: Container(
                                        padding: EdgeInsets.all(0),
                                        decoration: BoxDecoration(
                                          shape: BoxShape.circle,
                                        ),
                                        child: Center(
                                          child: Image.asset(
                                            mydata['UI']['icon'],
                                            height: 60.0,
                                            width: 60.0,
                                          ),
                                        ),
                                      ),
                                    ),
                                  ),
                                  onTap: () {
                                    Navigator.push(
                                      context,
                                      MaterialPageRoute(
                                          builder: (context) => api()),
                                    );
                                  }),
                              SizedBox(
                                width:30,
                              ),
                              Container(
                                margin: EdgeInsets.only(top: 30),
                                child: Text(
                                  mydata['UI']['title'],
                                  style: TextStyle(
                                      fontSize: 20,
                                      fontWeight: FontWeight.bold,
                                      color: Colors.white),
                                ),
                              ),
                            ],
                          ),
                        ],
                      ),
                      //-----------------------------------------------------
                      SizedBox(height: 30,),
                      Row(
                        children: <Widget>[
                          show(mydata['UI']['control'][0]['text'],
                              mydata ['UI']['control'][0]['icon']),
                          show(mydata['UI']['control'][1]['text'],
                              mydata ['UI']['control'][1]['icon']),
                          show(mydata['UI']['control'][2]['text'],
                              mydata ['UI']['control'][2]['icon']),

                        ],
                      ),
                      Row(
                        children: <Widget>[
                          show(mydata['UI']['control'][3]['text'],
                              mydata ['UI']['control'][3]['icon']),
                          show(mydata['UI']['control'][4]['text'],
                              mydata ['UI']['control'][4]['icon']),
                          show(mydata['UI']['control'][5]['text'],
                              mydata ['UI']['control'][5]['icon']),
                        ],
                      ),
                      Row(
                        children: <Widget>[
                          show(mydata['UI']['control'][6]['text'],
                              mydata ['UI']['control'][6]['icon']),
                          show(mydata['UI']['control'][7]['text'],
                              mydata ['UI']['control'][7]['icon']),
                          show(mydata['UI']['control'][8]['text'],
                              mydata ['UI']['control'][8]['icon']),

                        ],
                      ),
                      Row(
                        children: <Widget>[
                          show(mydata['UI']['control'][9]['text'],
                              mydata ['UI']['control'][9]['icon']),
                          show(mydata['UI']['control'][10]['text'],
                              mydata ['UI']['control'][10]['icon']),
                          show(mydata['UI']['control'][11]['text'],
                              mydata ['UI']['control'][11]['icon']),

                        ],
                      ),

                    ],
                  ),
                  ],
                )),
          );
        },
      ),
    );
  }
}


