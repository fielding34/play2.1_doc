play2.1_doc
===========

tips and documents for play 2.1


1. test enhancement

```Java 
    @Test
    public void testEnhancement() {
        SysUser user = SysUser.findById(1L);
        Assert.assertEquals("admin", user.userName);

        user.userName = "xxx"; // test failed
        //user.setUserName("xxx");  //compile complains, but test succeeded
        //SysUser.updeteUserName(user, "xxx");  //test succeeded
        Assert.assertEquals("after saving", "xxx", SysUser.findById(1L).userName);
    }

``` 

the Ebean objects in app directory will got enhancement after compiling, but those in test directory won't.
