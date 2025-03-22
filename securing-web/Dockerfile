# Etapa de construção
# Usar uma imagem Maven compatível com OpenJDK 21
FROM maven:3.9.6-eclipse-temurin-21 AS build

# Definir o diretório de trabalho
WORKDIR /app

# Copiar os arquivos do projeto
COPY securing-web/pom.xml /app/
COPY securing-web/src/ /app/src/

# Compilar o projeto
RUN mvn clean package -DskipTests

# Etapa de execução
FROM eclipse-temurin:21-jre
WORKDIR /app

# Copiar o JAR gerado
COPY --from=build /app/target/securing-web-0.0.1-SNAPSHOT.jar app.jar

# Expor a porta da aplicação
EXPOSE 8684

# Rodar a aplicação
ENTRYPOINT ["java", "-jar", "app.jar"]
