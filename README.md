#flask-note-4-SQL



Last login: Fri Aug 26 18:01:32 on ttys000
vinafu@192 ~ % cd Desktop
vinafu@192 Desktop % cd Flask_bLOG
vinafu@192 Flask_bLOG % LS
__pycache__	flaskblog.py	forms.py	static		templates
vinafu@192 Flask_bLOG % cd
vinafu@192 ~ % ls
Applications	Downloads	Movies		Public
Desktop		Environment	Music		get-pip.py
Documents	Library		Pictures
vinafu@192 ~ % cd Flask_Blog
cd: no such file or directory: Flask_Blog
vinafu@192 ~ % ls
Applications	Downloads	Movies		Public
Desktop		Environment	Music		get-pip.py
Documents	Library		Pictures
vinafu@192 ~ % cd Desktop
vinafu@192 Desktop % ls
8.20 写作课.docx		coding
Flask_Blog			files
FuWenjun-CV.docx		re-Eason's Timetable.docx
LTE + IELTS
vinafu@192 Desktop % cd Flask_Blog
vinafu@192 Flask_Blog % ls
__pycache__	flaskblog.py	forms.py	static		templates
vinafu@192 Flask_Blog % clear

vinafu@192 Flask_Blog % python  
zsh: command not found: python
vinafu@192 Flask_Blog % python3
Python 3.10.6 (v3.10.6:9c7b4bd164, Aug  1 2022, 17:13:48) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from flaskblog import db
/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/flask_sqlalchemy/__init__.py:872: FSADeprecationWarning: SQLALCHEMY_TRACK_MODIFICATIONS adds significant overhead and will be disabled by default in the future.  Set it to True or False to suppress this warning.
  warnings.warn(FSADeprecationWarning(
Traceback (most recent call last):
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/sql/schema.py", line 134, in _init_items
    spwd = item._set_parent_with_dispatch
AttributeError: 'function' object has no attribute '_set_parent_with_dispatch'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/Users/vinafu/Desktop/Flask_Blog/flaskblog.py", line 22, in <module>
    class Post(db.Model):      
  File "/Users/vinafu/Desktop/Flask_Blog/flaskblog.py", line 26, in Post
    content = db.Column(db.text, nullable=False)
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/sql/schema.py", line 1765, in __init__
    self._init_items(*args)
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/sql/schema.py", line 136, in _init_items
    util.raise_(
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/util/compat.py", line 208, in raise_
    raise exception
sqlalchemy.exc.ArgumentError: 'SchemaItem' object, such as a 'Column' or a 'Constraint' expected, got <function text at 0x1045757e0>
>>> db.create_all()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'db' is not defined
>>> exit()
vinafu@192 Flask_Blog % python3
Python 3.10.6 (v3.10.6:9c7b4bd164, Aug  1 2022, 17:13:48) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from flaskblog import db
/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/flask_sqlalchemy/__init__.py:872: FSADeprecationWarning: SQLALCHEMY_TRACK_MODIFICATIONS adds significant overhead and will be disabled by default in the future.  Set it to True or False to suppress this warning.
  warnings.warn(FSADeprecationWarning(
Traceback (most recent call last):
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/sql/schema.py", line 134, in _init_items
    spwd = item._set_parent_with_dispatch
AttributeError: 'function' object has no attribute '_set_parent_with_dispatch'

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/Users/vinafu/Desktop/Flask_Blog/flaskblog.py", line 22, in <module>
    class Post(db.Model):      
  File "/Users/vinafu/Desktop/Flask_Blog/flaskblog.py", line 26, in Post
    content = db.Column(db.text, nullable=False)
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/sql/schema.py", line 1765, in __init__
    self._init_items(*args)
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/sql/schema.py", line 136, in _init_items
    util.raise_(
  File "/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/sqlalchemy/util/compat.py", line 208, in raise_
    raise exception
sqlalchemy.exc.ArgumentError: 'SchemaItem' object, such as a 'Column' or a 'Constraint' expected, got <function text at 0x102c6d7e0>
>>> exit()
vinafu@192 Flask_Blog % python3
Python 3.10.6 (v3.10.6:9c7b4bd164, Aug  1 2022, 17:13:48) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from flaskblog import db
/Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/flask_sqlalchemy/__init__.py:872: FSADeprecationWarning: SQLALCHEMY_TRACK_MODIFICATIONS adds significant overhead and will be disabled by default in the future.  Set it to True or False to suppress this warning.
  warnings.warn(FSADeprecationWarning(
>>> db.create_all()
>>> from flaskblog import User, Post
>>> user_1 = User(username='Vina', email='v@demo.com, password='password' )
  File "<stdin>", line 1
    user_1 = User(username='Vina', email='v@demo.com, password='password' )
                                                                        ^
SyntaxError: unterminated string literal (detected at line 1)
>>> user_1 = User(username='Vina', email='v@demo.com', password='password' )
>>> db.session.add(user_1)
>>> user_2 = User(username='Oscar', email='o@demo.com, password='password' )
  File "<stdin>", line 1
    user_2 = User(username='Oscar', email='o@demo.com, password='password' )
                                                                         ^
SyntaxError: unterminated string literal (detected at line 1)
>>> user_2 = User(username='Oscar', email='o@demo.com', password='password' )
>>> db.session.add(user_2)
>>> db.session.commit()
>>> clear
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'clear' is not defined
>>> User.query.all()
[User('Vina','v@demo.com','default.jpg'), User('Oscar','o@demo.com','default.jpg')]
>>> User.query.first()
User('Vina','v@demo.com','default.jpg')
>>> User.query.filter_by(username='Vina').all()
[User('Vina','v@demo.com','default.jpg')]
>>> User.query.filter_by(username='Vina').first()
User('Vina','v@demo.com','default.jpg')
>>> user = User.query.filter_by(username='Vina').first()
>>> user
User('Vina','v@demo.com','default.jpg')
>>> user.id
1
>>> user = User.query.get(1)
>>> user
User('Vina','v@demo.com','default.jpg')
>>> user.posts
[]
>>> user.id
1
>>> post_1 = Post(title='Blog 1', content='First Post Content!', user_id=user.id)
>>> post_2 = Post(title='Blog 2', content='Second Post Content!', user_id=user.id)
>>> db.session.add(post_1)
>>> db.session.add(post_2)
>>> db.session.commit()
>>> user.posts
[<Post 1>, <Post 2>]
>>> for post in user.posts:
... print(post.title)
  File "<stdin>", line 2
    print(post.title)
    ^
IndentationError: expected an indented block after 'for' statement on line 1
>>> for post in user.posts:
...     print(post.title)
... 
Blog 1
Blog 2
>>> post = Post.query.first()
>>> 
>>> post
<Post 1>
>>> post.user_id
1
>>> post.author
User('Vina','v@demo.com','default.jpg')
>>> db.drop_all()
>>> db.create_all()
>>> User.query.all()
[]
>>> Post.query.all()
[]
>>> 
