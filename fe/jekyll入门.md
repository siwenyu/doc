# jekyll

使用步骤：
~ $ gem install jekyll
~ $ jekyll new myblog
~ $ cd myblog
~/myblog $ jekyll serve

浏览器打开： http://localhost:4000

1. 必须有以下环境：
	
	1. Ruby
	2. RubyGems
	3. Linux, Unix, or Mac OS X
	
可以使用'which ruby'检测是否安装，如果没有：[ruby](!http://www.ruby-lang.org/en/downloads/),[RubyGems
](!http://rubygems.org/pages/download)
2.安装时候有个报错，是缺少某个插件。忘了。。。。。。

1. 项目目录解析

.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html


1. _config.yml 配置文件
2. _drafts 草稿文件，没有添加配置和日期，干活。
3. _includes 公用文件：这个标签  {% include file.ext %} 来把文件 _includes/file.ext 包含进来。
4. _layouts 大布局
5. _posts 正式文章
6. _site 生成的目录文件
