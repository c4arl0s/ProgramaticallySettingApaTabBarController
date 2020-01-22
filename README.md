# ProgramaticallySettingApaTabBarController

# In AppDelegate

````swift 
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
```



