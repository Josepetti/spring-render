# Etapa de construção
# Usar uma imagem Maven compatível com OpenJDK 21
FROM maven:3.8.4-openjdk-21 AS build

# Definir o diretório de trabalho
WORKDIR /app

# Copiar os arquivos do projeto
COPY pom.xml /app/
COPY src/ /app/src/

# Compilar o projeto
RUN mvn clean package -DskipTests

# Etapa de execução
FROM openjdk:21-slim
WORKDIR /app

# Copiar o JAR gerado
COPY --from=build /app/target/securing-web-0.0.1-SNAPSHOT.jar app.jar

# Expor a porta da aplicação
EXPOSE 8684

# Rodar a aplicação
ENTRYPOINT ["java", "-jar", "app.jar"]
