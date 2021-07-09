# taobao_simc_login
Python利用selenium模拟登录淘宝

有前辈写过一些Python模拟登录淘宝的案例，具体实现的时候碰到了一些问题，主要包含以下两个问题：  
    1.截取登录图片后，pyautogui无法定位到登录界面的登录图片的坐标  
    2.获取到滑块的xpath之后，无法正常实现滑动  
    3.模拟登录需要用到chrome的驱动，[驱动地址(需翻墙)](https://sites.google.com/a/chromium.org/chromedriver/downloads)，根据浏览器版本选择合适的驱动版本下载即可
 
 于是修改了部分代码：  
    1.针对无法获取到登录图片坐标的问题，修改代码  
    ```
    pyautogui.locateOnScreen("login.png", confidence=0.5)
    ```  
    2.针对无法滑动滑块的问题，修改代码
    使用 Google 的Chrome Devtools-Protocol（cdp）能够避免被识别检测,需要注意的是低版本的chrome是不支持cdp的,需保持chrome版本在79以上  
    ```
    browser.execute_cdp_cmd("Page.addScriptToEvaluateOnNewDocument", {  
            "source": """Object.defineProperty(navigator, 'webdriver', {get: () => undefined})""",  
        })
    ```

觉得有用的小伙伴可以给个star呀~ ღ( ´･ᴗ･` )比心
