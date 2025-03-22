# Etapa de construção
# Usar uma imagem Maven compatível com OpenJDK 21
FROM maven:3.8.4-openjdk-21 AS build

# Definir o diretório de trabalho
WORKDIR /app

# Copiar os arquivos do projeto
COPY projeto/pom.xml /app/
COPY projeto/src/ /app/src/

# Compilar o projeto
RUN mvn clean package -DskipTests

# Etapa de execução
FROM openjdk:21-slim
WORKDIR /app

# Copiar o JAR gerado
COPY --from=build /app/target/*.jar app.jar

# Expor a porta
EXPOSE 8684

# Rodar a aplicação
ENTRYPOINT ["java", "-jar", "app.jar"]
