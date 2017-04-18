
O objetivo desta prática é aprender como configurar o Travis CI para fazer a integração contínua do projeto da disciplina em **3** ambientes distintos.

O projeto deve contar com, pelo menos, estas 3 branches:
- `master`
- `develop`
- `homolog`

## Branch DEVELOP

Essa branch é a que vai receber os commits durante o desenvolvimento das funcionalidades, e para correções de bugs eventuais. O Travis CI deve utilizar essa branch para rodar os testes de unidade e ignorar os testes de integração/sistema.

## Branch HOMOLOG

Essa branch vai receber versões parciais da aplicação, vindos a partir de merges da branch `DEVELOP` e rodar os testes de integração **1 vez ao dia**. Para isto, utilize o recurso **Cron Jobs** do Travis CI, a documentação está disponível em https://docs.travis-ci.com/user/cron-jobs/. Este recurso está ativado para os repositórios da organization da disciplina.

## Branch MASTER

A branch master vai armazenar apenas versões '**RELEASE**', ou seja, que estão prontas para **uso**. Sendo assim, ela deve receber merge de outras branches por meio de estratégia [`no-ff`] e ter `tags` para indicar que há uma nova versão lançada.

A configuração do Travis CI para realizar build apenas com tags pode ser encontrado em https://github.com/ads-ifpb-praticas/exemplo-profiles.

## Observações

Para ter arquivos `.travis.yml` diferentes em cada branch e não sofrer com problemas de conflitos ao realizar merge, veja como ignorar este arquivo com Git Attributes (https://git-scm.com/book/en/v2/Customizing-Git-Git-Attributes)

Caso ache necessário, utilize profiles do Maven para customizar arquivos de configuração de banco de dados entre os ambientes.

### Links úteis

http://stackoverflow.com/questions/9069061/what-is-the-difference-between-git-merge-and-git-merge-no-ff