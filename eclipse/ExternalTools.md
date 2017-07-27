#### 如何在eclipse中直接打开文件所在的文件夹
* Run->External Tools->External Tools Configurations-> Porgram->右键New
* Name命名，可以命名为OpenInExplorer
* Main->Location填写C:\Windows\explorer.exe
* Main->Arguments填写${container_loc}
* Common->Display in favorite menu选择External Tools使该项出现在工具栏中
* Apply完成
* 使用：Run->External Tools->OpenInExplorer就会直接打开当天编辑面板的文件所在的文件夹
