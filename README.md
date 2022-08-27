#flask-note-4-SQL

1） 需要在flaskblog.py里面编辑

            from datetime import datetime
            from flask_sqlalchemy import SQLAlchemy
            在顶上插入这个⬆️

            app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///site.db'
            统一资源标识符（Uniform Resource Identifier，URI)是一个用于标识某一互联网资源名称的字符串。 该种标识允许用户对任何（包括本地和互联网）的资源通过特定的协议进行交互操作。URL属于URI的子集。

            db = SQLAlchemy(app)

            class User(db.Model):
                id = db.Column(db.Integer, primary_key=True)
                username = db.Column(db.String(20), unique=True, nullable=False)
                email = db.Column(db.String(120), unique=True, nullable=False)
                image_file = db.Column(db.String(20), nullable=False, default='default.jpg')
                password = db.Column(db.String(60), nullable=False)
                posts = db.relationship('Post', backref='author',lazy=True)
                
                  unique=true 表示是独一无二的属性
                  nullable=false 表示不可以无效
                  注意：一般id = 是实数而且是primary key
                  最后一行表示关系：和下面表格post有关，所以这里首字母大写！
                  backref 表示建立一个新的column但是可以通过它来引用所有，可以从terminal里面看出来。
                  lazy 表示同意一次性从后面取出所有posts。
    
                def __repr__(self):
                    return f"User('{self.username}','{self.email}','{self.image_file}')"
                     
                     这一波指的是：展现出来的名字、邮箱、照片。有个f 
                   

            class Post(db.Model):      
                id = db.Column(db.Integer, primary_key=True)
                title = db.Column(db.String(100), nullable=False)
                date_posted = db.Column(db.DateTime, nullable=False, default=datetime.utcnow)
                content = db.Column(db.Text, nullable=False)
                user_id = db.Column(db.Integer, db.ForeignKey('user.id'), nullable=False)
                  
                  整体和上面一样，但是引入了时间，而且user_id是foreignkey。指的是table name？？？

            def __repr__(self):
                return f"Post('{self.title}','{self.date_posted}')"



2) 建立数据库，在terminal里面
一定要用terminal吗？
数据库找东西的方法
             
              vinafu@192 Flask_Blog % python3
              Python 3.10.6 (v3.10.6:9c7b4bd164, Aug  1 2022, 17:13:48) [Clang 13.0.0 (clang-1300.0.29.30)] on darwin
              Type "help", "copyright", "credits" or "license" for more information.
              >>> from flaskblog import db
              /Library/Frameworks/Python.framework/Versions/3.10/lib/python3.10/site-packages/flask_sqlalchemy/__init__.py:872: FSADeprecationWarning: SQLALCHEMY_TRACK_MODIFICATIONS adds significant overhead and will be disabled by default in the future.  Set it to True or False to suppress this warning.
                warnings.warn(FSADeprecationWarning(
              >>> db.create_all() ———— 建立全集
              >>> from flaskblog import User, Post ————这两个集
              >>> user_1 = User(username='Vina', email='v@demo.com', password='password' )   ————自己写
              >>> db.session.add(user_1)    ————session.add加入里面
              >>> user_2 = User(username='Oscar', email='o@demo.com', password='password' )
              >>> db.session.add(user_2)
              >>> db.session.commit()  ——————加入成功
              >>> User.query.all()  ——————可以查看里面的所有数据。all（）
              [User('Vina','v@demo.com','default.jpg'), User('Oscar','o@demo.com','default.jpg')]
              >>> User.query.first()  ——————查第几个用first（）或者second（）
              User('Vina','v@demo.com','default.jpg')
              >>> User.query.filter_by(username='Vina').all()  ——————有条件的查找，用filter_by同时讲清楚你在哪个范围里找，是all（）还是first（）？
              [User('Vina','v@demo.com','default.jpg')]
              >>> User.query.filter_by(username='Vina').first() 
              User('Vina','v@demo.com','default.jpg')
              >>> user = User.query.filter_by(username='Vina').first()
              >>> user
              User('Vina','v@demo.com','default.jpg')  ——————这里就来了，userid
              >>> user.id
              1
              >>> user = User.query.get(1) ————————get的用法，用了foreign key
              >>> user
              User('Vina','v@demo.com','default.jpg')
              >>> user.posts
              []
              >>> user.id
              1
              >>> post_1 = Post(title='Blog 1', content='First Post Content!', user_id=user.id) ——————建立post
              >>> post_2 = Post(title='Blog 2', content='Second Post Content!', user_id=user.id)
              >>> db.session.add(post_1)
              >>> db.session.add(post_2)
              >>> db.session.commit()
              >>> user.posts
              [<Post 1>, <Post 2>]
              >>> for post in user.posts: ————建好post后叫里面的内容
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
              >>> post.author ——————这里就是前面的backref， 可以引所有
              User('Vina','v@demo.com','default.jpg')
              >>> db.drop_all() ——————清理所有
              >>> db.create_all() ————————空集啦。
              >>> User.query.all()
              []
              >>> Post.query.all()
              []
              >>> 
