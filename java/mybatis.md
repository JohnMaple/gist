
> 二级缓存，一级缓存是默认开启

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
"http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.xx.xx.DemoDao">
    <!--开启当前namespace下的cache ，60s刷新一次-->
    <cache eviction="LRU" flushInterval="60000" size="512" readOnly="true"/>

    <resultMap id="ResultMap" type="com.xx.xx.xx.Demo">
        <id property="id" column="id" jdbcType="INTEGER"/>
    </resultMap>
</mapper>
```


> List参数

```xml
<select id="query" parameterType="com.xx.xx.PageRequest" resultMap="ResultMap">
select * from table_name t
<where>
<if test="customerIds != null and customerIds.size()>0">AND t.id in
    <foreach collection="customerIds" item="item" index="index" open="(" close=")" separator=",">#{item}</foreach>
</if>
</where>
</select>
```


> Map参数

```xml
<select id="query" parameterType="com.xx.xx.PageRequest" resultMap="ResultMap">
select * from table_name t
<where>
<if test="params != null">
    <foreach collection="params" index="key" item="value">
        <choose>
            <when test="key == 'id'">AND id != #{value}</when>
            <otherwise>
                AND ${key} = #{value}
            </otherwise>
        </choose>
    </foreach>
</if>
</where>
</select>
```


> 返回对象中包含另外一个对象

```xml
<resultMap id="ResultMap" type="com.xx.xx.Demo">
    <id property="id" column="id" jdbcType="INTEGER"/>
    <result property="name" column="name" jdbcType="VARCHAR"/>

    <association property="element" javaType="com.xx.xx.Element">
        <id property="id" column="e_id" jdbcType="INTEGER"/>
        <result property="name" column="e_name" jdbcType="VARCHAR"/>
    </association>
</resultMap>
```


> 返回对象中包含List（当前对象和子对象的id是必须的）

```xml
<resultMap id="ResultMap" type="com.xx.xx.Demo">
    <id property="id" column="id" jdbcType="INTEGER"/>
    <result property="name" column="name" jdbcType="VARCHAR"/>

    <collection property="elements" ofType="com.xx.xx.Element" javaType="java.util.ArrayList">
        <id property="id" column="e_id" jdbcType="INTEGER"/>
        <result property="name" column="e_name" jdbcType="VARCHAR"/>
    </collection>
</resultMap>
```


> 校验是否存在的通用查询语句

```xml
<select id="exist" parameterType="java.util.Map" resultType="java.lang.Integer">
    select count(1) from ad_creative_info
    <if test="params != null">
        <foreach collection="params" index="key" item="value">
            <choose>
                <when test="key == 'id'">AND id != #{value}</when>
                <otherwise>
                    AND ${key} = #{value}
                </otherwise>
            </choose>
        </foreach>
    </if>
</select>
```


> 日期格式化

```
select * from table_name where update_time = DATE_FORMAT(ad_date,"%Y-%m-%d %H:%i:%s")
```


> FIND_IN_SET

```
如果某个字段以逗号方式存储，例如element_ids=1,2,3,4,5，那么就可以使用FIND_IN_SET进行查找
select * from table_name where id > 100 and FIND_IN_SET(1,element_ids)
```