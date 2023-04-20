# Data Access Object
-------------
- ``` It is a design pattern that provides an abstraction layer between the application code and the underlying database```
- ```The purpose of DAO is to separate the code that interacts with the database from the rest of the application code, making it easier to manage and maintain.```
- ```The DAO pattern typically consists of a set of interfaces and classes that define the methods for performing CRUD (Create, Read, Update, Delete) operations on a database table. ```
- ```These interfaces and classes are responsible for creating, updating, deleting, and retrieving data from the database.```

## an example of a DAO interface for a User table:
```
public interface UserDao {
    public void createUser(User user);
    public User getUserById(int userId);
    public void updateUser(User user);
    public void deleteUser(int userId);
    public List<User> getAllUsers();
}
``` 
```The UserDao interface defines the methods for creating, updating, deleting, and retrieving user data from the database. The implementation of this interface will vary depending on the specific database technology being used, such as JDBC or Hibernate. ```

## example of a UserDao implementation using like JDBC:
```
public class JdbcUserDao implements UserDao {
    private <T> jdbcTemplate;

    public void setDataSource(<T> dataSource) {
        this.jdbcTemplate = new <T>(dataSource);
    }

    public void createUser(User user) {
        String sql = "INSERT INTO users (username, password, email) VALUES (?, ?, ?)";
        jdbcTemplate.update(sql, user.getUsername(), user.getPassword(), user.getEmail());
    }

    public User getUserById(int userId) {
        String sql = "SELECT * FROM users WHERE id = ?";
        User user = jdbcTemplate.queryForObject(sql, new Object[]{userId}, new UserMapper());
        return user;
    }

    public void updateUser(User user) {
        String sql = "UPDATE users SET username = ?, password = ?, email = ? WHERE id = ?";
        jdbcTemplate.update(sql, user.getUsername(), user.getPassword(), user.getEmail(), user.getId());
    }

    public void deleteUser(int userId) {
        String sql = "DELETE FROM users WHERE id = ?";
        jdbcTemplate.update(sql, userId);
    }

    public List<User> getAllUsers() {
        String sql = "SELECT * FROM users";
        List<User> users = jdbcTemplate.query(sql, new UserMapper());
        return users;
    }

    private static final class UserMapper implements RowMapper<User> {
        public User mapRow(ResultSet rs, int rowNum) throws SQLException {
            User user = new User();
            user.setId(rs.getInt("id"));
            user.setUsername(rs.getString("username"));
            user.setPassword(rs.getString("password"));
            user.setEmail(rs.getString("email"));
            return user;
        }
    }
}
```
- ``` the UserMapper class, the mapRow method is responsible for creating a User object and setting its properties based on the values in the ResultSet object.```
- ``` The ResultSet object represents a row in a database table, and the RowMapper interface provides a way to map the columns in the row to properties in a Java object```
- ```The JdbcUserDao class implements the UserDao interface using JDBC to interact with the database.```
- ``` The JdbcTemplate class is used to execute SQL queries and updates, and the RowMapper interface is used to map the results of a query to a Java object.```
- ``` The JdbcTemplate class is a core component of the Spring Framework's JDBC support.```
- ```It is a high-level abstraction layer on top of the JDBC API, providing a simplified and consistent interface for interacting with databases.```
- ```The JdbcTemplate class encapsulates much of the boilerplate code required for JDBC programming, such as opening and closing database connections, creating and executing statements, and processing result sets. ```
- ```This allows developers to focus on writing SQL queries and mapping the results to Java objects, without worrying about the low-level details of JDBC.```
