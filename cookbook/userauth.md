---
layout: default
title: user authentication
---

# user authentication

#I'm still working on this page, please no body else edit

##Problem
You want a system to authenticate users.

##Solution
A user authentication system is made up of a few parts. Adding users, logging users in, logging users out and checking if users are logged in. It also requires a database. For this example we'll be using MD5 and SQLite.

##
    def POST(self):
        i = web.input()

        authdb = sqlite3.connect('users.db')
        check = authdb.execute('select * from users where username=? and password=?', (i.username, i.password))
        if check: 
            session.loggedin = True
            session.username = i.username
            raise web.seeother('/results')   
        else: return render.base("Those login details don't work.")   
