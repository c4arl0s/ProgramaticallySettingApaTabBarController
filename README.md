# ProgramaticallySettingApaTabBarController

![Screen Shot 2020-01-22 at 0 52 45](https://user-images.githubusercontent.com/24994818/72871856-85ce7700-3cb1-11ea-8cdd-ae31409a0b3e.png)

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

![Screen Shot 2020-01-22 at 0 49 28](https://user-images.githubusercontent.com/24994818/72871879-9979dd80-3cb1-11ea-8516-99e36348eb7d.png)
