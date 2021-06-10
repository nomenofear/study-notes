## ע�������

Ŀ����Ϊ�˼����á�

Spring��ȫע�⿪����ע�����÷ǳ����ӣ�

- ʹ�õ���`SSM`�����Ļ�������XML+ע�������

  XML�������õ��������࣬ע�������Լ�������ࡣ

- ʹ�õ���`SpringBoot`����������ʹ��ȫע��



## 2. ����ע��

### 2.1 ע��ʹ�ò������

1. �������ɨ��

   ```xml
   <!--�������ɨ�裬ָ����Ӧɨ��İ�·�����ð������Ӱ������е��඼�ᱻɨ�裬���ذ���ָ��ע�����-->
   <context:component-scan base-package="com.itheima"/>
   ```

2. ��Ҫװ���Spring�������������ע��

   ```java
   @Component("userService")  // ���û��ָ��id��Ĭ��ʹ�õ�ǰ��������ĸСд��Ϊid
   public class UserServiceImpl implements UserService {}
   ```

3. ͨ��Spring���������ȡbean���󲢲���

   ```java
   // ��
   ```

4. ע��ʹ��ע������
   �ڽ��������ɨ��ʱ��������õİ������Ӱ��������ļ�����ɨ��
   ɨ����������ļ��еݹ��������ʽ���е�
   ɨ����̽���ȡ�Ϸ���java�ļ�
   ɨ��ʱ����ȡspring��ʶ���ע��
   ɨ�������Ὣ��ʶ�����Чע��ת��Ϊspring��Ӧ����Դ����Spring����

5. ���ɨ��֮�ų�

   ```xml
   <!--�������ɨ�裬ָ����Ӧɨ��İ�·�����ð������Ӱ������е��඼�ᱻɨ�裬���ذ���ָ��ע�����-->
   <context:component-scan base-package="com.itheima">
       <!-- ��ɨ��ָ�������� -->
       <!-- �ų���ע��ָ��ע����� -->
       <context:exclude-filter type="annotation"
                               expression="org.springframework.stereotype.Controller"/>
   
      
       <context:exclude-filter type="custom" expression="com.itheima.web"/>
   </context:component-scan>
   ```

   

### 2.2 ����ע�⼰����

| ע��                                 |        | ��ͬ��                         | ����                           | ��ע                               |
| ------------------------------------ | ------ | ------------------------------ | ------------------------------ | ---------------------------------- |
| <font color="red">@Component</font>  | ����   | bean��ǩ                       | �ѵ�ǰ��װ���Spring����       | Ĭ����������Ϊid<br>��������ĸСд |
| <font color="red">@Controller</font> | ����   | bean��ǩ                       | ͬ@Component                   | ���廯��@Component                 |
| <font color="red">@Service</font>    | ����   | bean��ǩ                       | ͬ@Component                   | ���廯��@Component                 |
| <font color="red">@Repository</font> | ����   | bean��ǩ                       | ͬ@Component                   | ���廯��@Component                 |
| <font color="red">@AutoWired</font>  | ������ | `property[ref]`                | ��Spring������Ѱ�Ҷ���ע��     | ע�벻����setter                   |
| <font color="red">@Value</font>      | ������ | `property[value]``             | Ϊ��ͨ��������ע������         | ע�벻����setter                   |
| @Qualifier                           | ������ | ���@AutoWiredʵ�ְ�������ע�� | ���@AutoWiredʵ�ְ�������ע�� |                                    |
| @Resource                            | ������ | =@AutoWired + @Qulifier        | ��������ע��                   | jdk9�����ϰ汾Ĭ�ϲ�֧��           |
| @Scope                               | ����   | bean��ǩscope����              | bean��singleton\|prototype     | Ĭ��Singleton                      |
| @PostConstruct                       | ������ | `init-method`����              | ��ע��ʼ������                 |                                    |
| @PreDestroy                          | ������ | `destroy-method`               | ��ע���ٷ���                   | �������ٲ��ܿ���                   |
|                                      |        |                                |                                |                                    |
|                                      |        |                                |                                |                                    |
|                                      |        |                                |                                |                                    |
|                                      |        |                                |                                |                                    |
|                                      |        |                                |                                |                                    |
| @Primary                             | ������ | property[index=0]              |                                |                                    |
| @lazy@dependenson                    |        |                                |                                |                                    |



### 2.3 @AutoWired

���ã���������ע��

**����ԭ��**

�����ݱ� ��ע�����Ե����ͣ���Spring�����в����Ƿ��з���Ҫ���bean����

- ����������ֻ��һ����������Ҫ���bean��ֱ��ע��
- ���������Ҵ��ڶ����������Ҫ���bean������ݳ�Ա�������������е�beanId����ƥ�䣬ƥ��ɹ���ע��
- ƥ��ʧ�ܣ��ͱ�����ʾ��Ҫ������������ �����ֱַ���ʲô�������Ҷ��ò��ˡ�

```java
@Autowired
private UserDao userDao;
```



### 2.4 @Qualifier 

���ã����@AutoWired��ͬʵ�֣���������ע��



```java
@Autowired
@Qualifier("userDao")
private UserDao userDao;
```



### 2.5 @Resource

��ͬ��`@Autowired + @Qualifier`����������javax��չ����Java9�����ϰ汾Ĭ�ϲ�������չ������������Ҫ�ֶ���Ӳ����á�



### 2.6 ���������ע��

�����У�Ϊ��ǰ���Ա����ע�룬ʹ��`@Autowired`





### 2.7 @Value

- ע����ͨ���������� �������� + String
- �������SpELl��ȡ�����ļ�������



## 3. ȫע�⿪��Spring

### 3.1 @Bean

���ã�װ���������

����һ���������÷����ķ���ֵ�������������Ķ���

�������������У�Ҫȥ���ܱ�Springʶ�𣬷���������Ч������Ҫ�����ϼ�һ��`@Component`����ʱ������

```java
@Component  //��ʱ��ʽ�����ڻ����
public class JDBCConfig {
    /**
     * @Bean ��ע�ڷ����ϣ���ѵ�ǰ�����ķ���ֵװ���Spring����������ָ��ID��
     * ���û��ָ��id���Է�������Ϊid��
     * ͨ������£����ǵķ�������ʡ��get��ֱ��дdataSource
     * @return
     */
    // @Bean  ���ʱ��û���ֶ�ָ��id��Ĭ��ʹ�õ�ǰ��������Ϊid
    @Bean("dataSource")
    public static DruidDataSource dataSource(){
        
        // ��ȡproperties�����ļ�
        
        DruidDataSource ds = new DruidDataSource();
        ds.setDriverClassName("com.mysql.jdbc.Driver");
        ds.setUrl("jdbc:mysql://localhost:3306/spring_db");
        ds.setUsername("root");
        ds.setPassword("itheima");
        return ds;
    }
}
```



> ע�⣺

������Ҫ��Ӳ������Java�����У������ֶ���ȡproperties�����ļ�������ʹ��ע�����properties�����ļ���

### 3.2 @PropertySource

���ã�ע������properties�ļ�







### 3.3 @ComponentScan

���ã�ע�⿪�����ɨ��

**������**   ����� ����ԭ����   **�����ļ�**

@ComponentScan("basePackage")



- ��ɨ��ָ������

  ```java
  @ComponentScan(value = "com.itheima",
                 excludeFilters = {@ComponentScan.Filter({Controller.class})})
  @ComponentScan(value = "com.itheima",
                 excludeFilters = {
                     @ComponentScan.Filter(
                         type= FilterType.CUSTOM,
                         pattern = "com.itheima.web")})
  public class SpringConfig {}
  ```

  

  

  

### 3.5











### 3.x ����ע�⼰����



| ע��            | ��עλ�� | ��ͬ��                                        | ����                   | ��ע               |
| --------------- | -------- | --------------------------------------------- | ---------------------- | ------------------ |
| @Bean           | ����     | `<bean>`                                      | װ�����������         | Ĭ���Է�������Ϊid |
| @PropertySource | ��       | `<context:property-placeholder location=""/>` | ����properties�����ļ� |                    |
| @ComponentScan  | ��       | `<context:component-scan package=""/>`        | �������ɨ��           |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |
|                 |          |                                               |                        |                    |

















## Bean�ļ��ؿ���

## ʹ��ע��װ���������

## Spring����junit

## `IoC`�ײ����ԭ��