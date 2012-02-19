Subtree merge for RbST
**********************

- use subtree merge to add RST parsing to blog::

    git clone git@github.com:faircloth-lab/blog-theme.git faircloth-lab-blog
    git remote add jekyll-rst-remote https://github.com/xdissent/jekyll-rst.git
    git checkout -b jekyll-rst-branch jekyll-rst-remote/master
    git checkout master
    git read-tree --prefix=_plugins/jekyll-rst -u jekyll-rst-branch

RVM
***

	bash -s stable < <(curl -s https://raw.github.com/wayneeseguin/rvm/master/binscripts/rvm-installer )
	type rvm | head -1
	rvm requirements
	rvm install 1.9.3
	rvm use ruby-1.9.3-p0 --default
	gem install jekyll
	rvm info


