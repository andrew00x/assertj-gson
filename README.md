Very basic AssertJ assertions for Gson

Usage example:

```java

import static com.andrew00x.assertj.json.gson.JsonAssertions.assertThat;

public class UserTest {
    /*
    Json:
    {
        "firstName": "Frodo",
        "lastName": "Baggins",
        "profile": {
            "age": 23
            ....
        }
    } 
    */
    @Test
    public void testUser() {
        JsonElement data = ...
        assertThat(data).hasField("firstName").asString().isEqualTo("Frodo");
        assertThat(data).hasField("lastName").asString().isEqualTo("Baggins");
        assertThat(data).hasField("profile").hasField("age").asInt().isEqualTo(23);
        // or 
        assertThat(data).hasPath("profile", "age").asInt().isEqualTo(23);
    }
}
```