[chapter Field]

Manipulacão de Fields usando o Mirror. No Mirror, a pesquisa dos atributos também é feita
nas superclasses e nas interfaces.

[section Refletindo]

Refletir um atributo através do nome (devolverá null se não encontrar):

[java]
Class clazz;
Field f = new Mirror().on(clazz).reflect().field("nomeAtributo");
[/java]

Refletir todos os campos de uma classe (devolverá uma lista vazia se não encontrar fields):

[java]
Class clazz;
List<Field> l = new Mirror().on(clazz).reflectAll().fields();
[/java]

Refletir todos os campos de uma classe que sejam aceitos por um Matcher<Field>(devolverá uma lista vazia se não encontrar fields):

[java]
Class clazz;
List<Field> l = new Mirror().on(clazz).reflectAll().fields()
                                 .matching(new SeuProprioMatcher());
[/java]

Você também pode mapear seus campos para outros tipos:

[java]
Class<T> clazz;
List<String> l = new Mirror().on(clazz).reflectAll()
                      .fields().mappingTo(new SeuProprioMapperDeFieldParaString());
[/java]

[section Atribuindo Valores]

Atribuindo valores em um atributo estático:

[java]
Class clazz;
new Mirror().on(clazz).set().field("nomeAtributo").withValue(valor);
[/java]

Atribuindo valor em um atributo de instância:

[java]
Object target;
new Mirror().on(target).set().field("nomeAtributo").withValue(valor);
[/java]

Você também pode passar um java.lang.reflect.Field ao invés de uma String com o nome do atributo

Atribuindo valores em um atributo estático:

[java]
Field umAtributo;
Class clazz;
new Mirror().on(clazz).set().field(umAtributo).withValue(valor);
[/java]

[section Lendo Valores]

Recuperando valor de um atributo estático:

[java]
Class clazz;
Object value = new Mirror().on(clazz).get().field("nomeAtributo");
[/java]

Recuperando valor de um atributo de instância:

[java]
Object target;
Object value = new Mirror().on(target).get().field("nomeAtributo");
[/java]

Você também pode passar um java.lang.reflect.Field ao invés de uma String com o nome do atributo.

Recuperando valor de um atributo estático:

[java]
Field umAtributo;
Class clazz;
Object value = new Mirror().on(clazz).get().field(umAtributo);
[/java]