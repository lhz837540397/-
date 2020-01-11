from selenium import webdriver  # 导入web驱动库
import time  # 导入时间库

# 采集地址
URL = 'https://www.toutiao.com/ch/news_finance/'
# 翻页次数，每页大约10条
PAGE = 50

# 启动webdrive
# 指定webdriver路径
driver = webdriver.Chrome(executable_path=r'C:\Program Files (x86)\Google\Chrome\Application\chromedriver.exe')
driver.get(URL)
driver.implicitly_wait(10)
driver.maximize_window()  # 最大化窗口
driver.implicitly_wait(10)

list = []

# 通过下拉进度条一直加载页面
def getPage():
    # 滚屏
    driver.execute_script("window.scrollTo(0,1000);")
    time.sleep(1)

    # 每页加载10条，需要翻页
    for i in range(PAGE):
        driver.execute_script("window.scrollTo(0,document.body.scrollHeight);")
        time.sleep(2)
    getList()
    driver.close()

# 获取页面新闻标题，详情页面链接，来源，评论，并添加到列表中
def getList():
    # 找到每个li
    lis = driver.find_elements_by_xpath('.//div[@class="wcommonFeed"]/ul/li[@class="item"]')
    print('共采集' + str(len(lis)) + '条记录')
    for li in lis:
        try:
            titleBox = li.find_element_by_xpath('.//div[@class="title-box"]/a')
            title = titleBox.text
            url = titleBox.get_attribute('href')
            source = li.find_element_by_xpath('.//a[@class="lbtn source"]').text
            comment = li.find_element_by_xpath('.//a[@class="lbtn comment"]').text
            time = li.find_element_by_xpath('.//div[@class="y-left"]//span[@class="lbtn"]').text

            data={
                '标题': title,
                'url': url,
                '来源': source,
                '评论': comment,
                '发布时间': time,
            }
            #print(data)
            list.append(data)
        except Exception as e:
            print(e)

    print('共成功解析' + str(len(list)) + '条记录')

def main():
    getPage()

if __name__=="__main__":
    main()
