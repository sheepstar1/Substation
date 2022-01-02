# Substation
功能介绍：
模块一：文件格式转换模块
支持文件类型为xlsx或xls与csv文件类型之间的相互转换，该模块以第三方库xlrd、codecs、csv以及pandas四个库组成实现，通过以分行读取目标文件，并将按行读取的内容写入内存，最终保存到新文件实现格式转换。
# excel文件转换为csv文件
def xlsx_to_csv(path):
    workbook = xlrd.open_workbook(path)
    table = workbook.sheet_by_index(0)
    name = input("转换之后的文件名：")
    with codecs.open(f'{name}.csv', 'w', encoding='utf-8') as f:
        write = csv.writer(f)
        for row_num in range(table.nrows):
            row_value = table.row_values(row_num)
            write.writerow(row_value)
    print()


# csv文件转为excel文件
def csv_to_xlsx(path):
    csv_1 = pd.read_csv(path, encoding='utf-8')
    file_name = input("转换之后的文件名：")
    sheet_name = input("第一张表格的名字：")
    csv_1.to_excel(f'{file_name}.xlsx', sheet_name=f'{sheet_name}')
    print("转换成功")
    print()

模块二：文件读取
本模块支持读取excel文件以及csv文件，并在终端输出展示部分文件内容，此外，该模块所需的库只有pandas一个。
# 读取excel文件
def read_xlsx(path):
    data = pd.read_excel(path)
    print("获取到的数据为：")
    print(data.values)
    print()


# 读取csv文件
def read_csv(path):
    data = pd.read_csv(path)
    print("获取到的数据为：")
    print(data)
    print()

模块三：功能选择
# 功能菜单
def menu():
    while True:
        print("—————————————功能选择———————————")
        print("1.文件转换")
        print("2.文件读取")
        print("3.退出程序")
        choice = input("请输入您的选择：")
        if choice == '1':
            print("选择转换类型：")
            print("1.excel转为csv")
            print("2.csv转为excel")
            choice1 = input("选择准换类型：")
            if choice1 == '1':
                path_xlsx = input(r"请输入文件地址(格式为：C:\xxx\xxx\xxx.xlsx)：")
                xlsx_to_csv(path_xlsx)
            elif choice1 == '2':
                path_csv = input(r"请输入文件地址(格式为：C:\xxx\xxx\xxx.csv)：")
                csv_to_xlsx(path_csv)

        if choice == '2':
            print("选择读取类型：")
            print("1.excel")
            print("2.csv")
            choice2 = input("选择读取类型：")
            if choice2 == '1':
                path_xlsx = input(r"请输入文件地址(格式为：C:\xxx\xxx\xxx.xlsx)：")
                read_xlsx(path_xlsx)
            elif choice2 == '2':
                path_csv = input(r"请输入文件地址(格式为：C:\xxx\xxx\xxx.csv)：")
                read_csv(path_csv)

        if choice == '3':
            print("欢迎下次使用")
            break
以while循环嵌套if条件语句的形式，选择用户所需的功能。

运行方式：
直接运行主函数：
if __name__ == '__main__':
    menu()
即可进入程序选择。

运行截图
 
 
 
