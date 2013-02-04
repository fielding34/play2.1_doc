play2.1_doc
===========

tips and documents for play 2.1


test enhancement
====

```Java 
    @Test
    public void testEnhancement() {
        SysUser user = SysUser.findById(1L);
        Assert.assertEquals("admin", user.userName);

        user.userName = "xxx"; // 1. test failed
        //user.setUserName("xxx");  //2. compile complains in IDE, but test succeeded
        //SysUser.updeteUserName(user, "xxx");  //3. test succeeded
        Ebean.save(user);
        Assert.assertEquals("after saving", "xxx", SysUser.findById(1L).userName);
    }

``` 

1. The Ebean objects in app directory will got magic enhancement during compiling, but those in test directory won't;
2. There is no explicitly setUserName in SysUser object, so you will get compile error;
    But play will compile app directory first and add getter and setter for each model, so test passed;
3. Add a method into app directly to use automatic magic enhancement;
