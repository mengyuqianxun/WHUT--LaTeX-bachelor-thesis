# WHUT--LaTex-bachelor-thesis

## 简介

&emsp;&emsp;本模板是[武汉理工大学](http://www.whut.edu.cn/)本科生毕业论文LaTex模板，主要参考了曹宇学长的方法，[原模板传送门](https://github.com/tsaoyu/WHUT-LaTeX-bachelor)。虽然进行了不少的修改，但本模板还是存在一些问题，特别是用了一页废页来维持页面设置。 如果你有关于本模板的良好意见和建议，请在顶栏的问题(issue)一栏中提出。



2020.7.16更新

***

&emsp;&emsp;经过了自身的毕业答辩，对本模板作出最后一次更新。更新内容如下：



&emsp;&emsp;**注释:**在撰写论文和降重过程中，切记不要随意删除内容，将待考量内容放入注释中。

&emsp;&emsp;由于%也有注释效果，但考虑到内容等注释(eg.下面介绍时间序列特点)和正文待考量内容的区别，我分别选择用%和\begin{comment}、\end{comment}来区分彼此。

```
% 注释内容

\usepackage{verbatim}	%多行注释宏包

\begin{comment}	%使用方法
	一、
	二、
	三、
\end{comment}
```



&emsp;&emsp;**三线表:**论文中所有的表都要使用三线表，除了最基础的表，还可以根据需要绘制进阶表。此处提供一个Latex在线表格网站：[Tables Generator](https://www.tablesgenerator.com/)。

```latex
\usepackage{booktabs}
%三线表格中的上中下直线线型设置宏包

\begin{table}[h]
	\centering
	\caption{北京PM2.5数据集特征}
	\label{table:4.1}
	\begin{tabular}{cccccccc}
		\toprule  %添加表格头部粗线
		pm2.5 & DEWP & TEMP & PRES & cbwd & lws & ls & lr \\
		\midrule  %添加表格中横线
		PM2.5浓度 & 露点 & 温度 & 大气压 & 风向 & 风速 & 累积雪量 & 累积雨量 \\
		\bottomrule %添加表格底部粗线
	\end{tabular}
\end{table}
```

![table1](README_figure\table1.png)

```latex
\begin{table}[!htbp]
	\renewcommand\arraystretch{1.3}
	\centering
	\caption{模型性能综合比较}
	\label{table:4.5}
	\begin{tabular}{cccccc}
		\toprule
		
		\multicolumn{1}{c}{ \multirow{3}*{模型} }& \multicolumn{4}{c}{数据集} \\
		\cline{2-6}
		\multicolumn{1}{c}{} &\multicolumn{2}{c}{数据集1}& & \multicolumn{2}{c}{数据集2}\\
		\multicolumn{1}{c}{} &MAE &RMSE& &MAE &RMSE \\
		\midrule  
		A&14.79&20.84& &20.73&35.45\\
		
		B&13.35&17.3& &12.35&21.22\\
			
		C&12.61&16.77& &12.2&21.85\\
			
		D&10.39&15.53& &11.88&21.36\\
		\bottomrule
	\end{tabular}
\end{table}
```

![table2](README_figure\table2.png)



&emsp;&emsp;**图:**用以下三个命令将Latex中默认的(图1.1：第一张图)改为论文正确的(图1.1  第一张图)。即不使用冒号，改为两个半角空格。

```
/usepackage{caption}

/DeclareCaptionLabelSeparator{twospace}{/ ~}
/captionsetup{labelsep=twospace}
```



&emsp;&emsp;**目录：**将目录中的字体按照要求进行更改。

```
%====================目录======================
\usepackage{titletoc}
\titlecontents{section}[3.8em]
{\songti\zihao{-4}}
{\contentslabel{4em}}{\hspace*{-4em}}
{~\titlerule*[0.8pc]{$.$}~\contentspage}
```



&emsp;&emsp;**文献:**由于通过Bib经过Latex生成的文献，格式非常混乱，本人也被老师一顿猛批。因此，本人放弃了自动生成文献，转而将整理好的文献放入Latex中。

&emsp;&emsp;文献的具体要求详情见**《本科生毕业设计(论文)撰写规范和示例》->三、撰写要求->(19) 参考文献**。部分内容如下：

&emsp;&emsp;参考文献的著录应符合国家标准，参考文献的序号左顶格，并用数字加方括号表示，与正文中的引文标示一致，如[1]，[2]……。每一条参考文献著录均以“.”结束。多位作者，姓名写到第三位，余者写“，等”或“，et al.”。 

&emsp;&emsp;①文献是期刊时，书写格式： 
&emsp;&emsp;[序号]  作者.题目[J].  刊名，年，卷号（期号）起止页码.  或年（期号）：起止页码. 

```
%====================参考文献上标==========================
\newcommand{\upcite}[1]{\textsuperscript{\textsuperscript{\cite{#1}}}}

%正文中
一二三\upcite{zhongwen1}。 %引用要在句号之前，{}内与appendices.tex中一致，自己命名
三四五\upcite{Guo-4}。

%appendices.tex
\newpage
\appendix
\begin{thebibliography}{99}
\songti\zihao{5}

\bibitem{zhongwen1}刘颉羲, 陈松灿. 基于混合门单元的非平稳时间序列预测[J]. 计算机研究与发展, 2019, 56(8): 1642 – 1651.
\bibitem{Guo-4}Guo J, Xie Z, Qin Y, et al. Short-Term Abnormal Passenger Flow Prediction Based on the Fusion of SVR and LSTM[J]. IEEE Access, 2019, 7 : 42946–42955. 

\end{thebibliography}
```

&emsp;&emsp;参考文献需要仔细检查，推荐使用**百度学术**中的**引用**，复制GB/7714中内容，优点是只需要文献名称和浏览器。如果特殊文献没有，可以下载bib文件，自己依照撰写要求中的文献标准进行仿写，力求完全无误。

![bibliography](README_figure\bibliography.png)



&emsp;&emsp;**数学公式：**数学公式是每个人都比较头疼的内容。本人撰写论文过程中使用的是MathType。设置方法如下：选项——>剪切和复制选项——>转换其他文字：Latex 2.09 and later。复制出来的就是公式的Latex版本。优点是：自己通过菜单上的自己编辑公式，缺点是：如果公式形式混乱，Latex显示会出现问题，需要费力修改。

&emsp;&emsp;在这里再推荐一个神奇的软件：mathpix snip，通过截图数学公式来自动识别、生成代码。



&emsp;&emsp;以上就是本次更新的全部内容，希望喜欢的校友可以star一下。最后，再次感谢王啸雄同学在这期间的交流和帮助，同时，再次感谢曹宇学长对初代模板的贡献。