class DartIsolate extends StatelessWidget {
  const DartIsolate({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: AppColors.whiteColor,
      appBar: AppBar(
        backgroundColor: AppColors.whiteColor,
        title: Image.asset(
          AppImagePaths.appLogo2,
          fit: BoxFit.cover,
          height: 50,
          width: 200,
        ),
        centerTitle: true,
      ),
      body: SingleChildScrollView(
        child: Padding(
          padding: Dimensions.kAppPadding,
          child: Container(
            padding: EdgeInsets.only(top: 28.h),
            child: Column(
              crossAxisAlignment: CrossAxisAlignment.start,
              children: <Widget>[
                Center(child: Helpers.appLoader()),
                VSpace(30.h),
                CustomButton(
                  text: "WithoutIsolate",
                  bgColor: AppColors.mainColor,
                  onTap: () {
                    var total = 0.0;
                    for (var i = 0; i < 600; i++) {
                      total += i;
                      print(total);
                    }
                  },
                ),
                VSpace(30.h),
                CustomButton(
                  text: "WithIsolate",
                  bgColor: AppColors.mainColor,
                  onTap: () async {
                    var receivePort = ReceivePort();
                    await Isolate.spawn(createTask, receivePort.sendPort);
                    receivePort.listen((total) {
                      print(total);
                    });
                  },
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }
}

createTask(SendPort sendPort) {
  var total = 0.0;
  for (var i = 0; i < 600; i++) {
    total += i;
    print(total);
  }
  return sendPort.send(total);
}
