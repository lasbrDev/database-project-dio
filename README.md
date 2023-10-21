# Bootcamp Database Experience - E-commerce and University

In this repository, you will find SQL scripts to create the databases for an e-commerce system and a university. These scripts were part of the hands-on project in the "Database Experience" bootcamp by Digital Innovation One, led by instructor Juliana Mascarenhas.

## Instructor
- **Instructor**: Juliana Mascarenhas
- **Bootcamp**: Database Experience - Digital Innovation One

## E-commerce

The e-commerce database comprises tables related to vendors, products, customers, orders, and payments.

### Tables

1. **Vendedor_Terceiro**: Stores information about third-party vendors.

2. **Product**: Contains details about available products.

3. **Product_por_Vendedor**: Records the relationship between products and vendors.

4. **Fornecedor**: Holds information about suppliers.

5. **Disponibiliza_Produto**: Associates products with suppliers.

6. **Estoque**: Contains inventory information.

7. **Relacao_Produto_Estoque**: Defines the relationship between products and inventory.

8. **PJ and PF**: Tables for legal entities (Pessoa Jurídica) and individuals (Pessoa Física).

9. **Debito_Online, Credito, and Boleto**: Record payment information.

10. **Pagamento**: Links payments to various payment methods.

11. **Cliente**: Stores customer information.

12. **Pedido**: Contains order details.

13. **Relacao_Produto_Pedido**: Defines the relationship between products and orders.

## University

The university database includes tables related to students, professors, courses, disciplines, and course offerings.

### Tables

1. **Enderecos**: Stores address information.

2. **Pessoas**: Contains details about individuals, including students and professors.

3. **Alunos and Professores**: Tables that extend the "Pessoas" table.

4. **Departamentos**: Records academic department information.

5. **Cursos**: Contains academic course details.

6. **Disciplinas**: Records discipline details.

7. **Periodos**: Contains academic period information.

8. **Oferta_Disciplinas**: Associates disciplines with professors and academic periods.

9. **Alunos_Matriculados_Cursos**: Records the relationship between students and courses.

10. **Extensões and Extensões_has_Alunos**: Tables related to academic extension activities.

11. **Financeiro**: Records financial information related to tuition and salaries.

12. **Pre_Requisitos and Pre_Requisitos_Disciplinas**: Tables for discipline prerequisites.

## Running the Scripts

To create the databases and their tables, you can run the SQL scripts provided in your database management system (in this Bootcamp MySQL and Workbench were used).

Ensure that you create the database first and then run the scripts to create the tables.

## License

This project is licensed under the **MIT License**.

---

Feel free to use these scripts in your projects or as a starting point to create your own databases. If you have any questions or need additional assistance, please don't hesitate to reach out.


