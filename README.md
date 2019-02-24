# ProgramaticallySettingApaTabBarController
````swift 
//ProgramaticallySettingApaTabBarController
//
//  AppDelegate.swift
//  ProgramaticallySettingApaTabBarController
//
//  Created by Carlos Santiago Cruz on 17/10/18.
//  Copyright © 2018 Carlos Santiago Cruz. All rights reserved.
//

import UIKit

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    var window: UIWindow?


    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        window = UIWindow(frame: UIScreen.main.bounds)
        let storyboard = UIStoryboard(name: "MyMain", bundle: nil)
        let firstViewController = storyboard.instantiateViewController(withIdentifier: "firstViewController")
        let secondViewController = storyboard.instantiateViewController(withIdentifier: "secondViewController")
        let thirdViewController = storyboard.instantiateViewController(withIdentifier: "thirdViewController")
        let tabBarController = UITabBarController()
        tabBarController.viewControllers = [firstViewController, secondViewController, thirdViewController]
        window?.rootViewController = tabBarController
        window?.makeKeyAndVisible()
        firstViewController.tabBarItem.title = "Controller 1"
        secondViewController.tabBarItem.title = "controller 2"
        thirdViewController.tabBarItem.title = "controller 3"
        return true
    }


    func applicationWillResignActive(_ application: UIApplication) {
        // Sent when the application is about to move from active to inactive state. This can occur for certain types of temporary interruptions (such as an incoming phone call or SMS message) or when the user quits the application and it begins the transition to the background state.
        // Use this method to pause ongoing tasks, disable timers, and invalidate graphics rendering callbacks. Games should use this method to pause the game.
    }

    func applicationDidEnterBackground(_ application: UIApplication) {
        // Use this method to release shared resources, save user data, invalidate timers, and store enough application state information to restore your application to its current state in case it is terminated later.
        // If your application supports background execution, this method is called instead of applicationWillTerminate: when the user quits.
    }

    func applicationWillEnterForeground(_ application: UIApplication) {
        // Called as part of the transition from the background to the active state; here you can undo many of the changes made on entering the background.
    }

    func applicationDidBecomeActive(_ application: UIApplication) {
        // Restart any tasks that were paused (or not yet started) while the application was inactive. If the application was previously in the background, optionally refresh the user interface.
    }

    func applicationWillTerminate(_ application: UIApplication) {
        // Called when the application is about to terminate. Save data if appropriate. See also applicationDidEnterBackground:.
    }


}
```

``` swift 
import UIKit

class Item: NSObject {
    var name: String
    var valueInDollars: Int
    var serialNumber: String?
    let dateCreated: Date
    // A designated initializer is a primary initializer for the class.
    // Every class has at least one designated initializer.
    init(name: String, serialNumber: String?, valueInDollars: Int) {
        self.name = name
        self.valueInDollars = valueInDollars
        self.serialNumber = serialNumber
        self.dateCreated = Date()
        super.init()
    }
}
```

``` swift 
import Foundation

extension Item {
    // convenience initializers are optional.
    convenience init(random: Bool = false) {
        if random {
            let adjectives = ["Fluffy", "Rusty", "Shiny", "Good", "New", "First", "Last", "Long" ]
            let nouns = ["Bear", "Spork", "Mac", "iphone", "cat", "T.V"]
            var idx = arc4random_uniform(UInt32(adjectives.count))
            let randomAdjective = adjectives[Int(idx)]
            idx = arc4random_uniform(UInt32(nouns.count))
            let randomNoun = nouns[Int(idx)]
            let randomName = "\(randomAdjective) \(randomNoun)"
            let randomValue = Int(arc4random_uniform(100))
            let randomSerialNumber = UUID().uuidString.components(separatedBy: "-").first!
            self.init(name: randomName, serialNumber: randomSerialNumber, valueInDollars: randomValue)
        } else {
            self.init(name: "", serialNumber: nil, valueInDollars: 0)
        }
    }
}
```
``` swift 
import UIKit

// ItemStore is a Swift base class – it does not inherit from any other class.
// Unlike the Item class that you defined earlier, ItemStore does not require any of the behavior that NSObject affords.
class ItemStore {
    var items = [Item]()
    
    init() {
        for _ in 0..<10 {
            createItem()
        }
    }
    
    // @discardableResult annotation means that a caller of this function is free to ignore the result of calling this function.
    // https://github.com/apple/swift-evolution/blob/master/proposals/0047-nonvoid-warn.md
    
    @discardableResult func createItem() -> Item {
        let newItem = Item(random: true)
        items.append(newItem)
        return newItem
    }
}
```

