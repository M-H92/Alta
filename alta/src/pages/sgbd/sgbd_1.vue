<template>
  <section>
    <h1>
      Première création d'une
      <abbr class="db-tooltip tooltip" title="DataBase => Base de données"
        >DB</abbr
      >
    </h1>
    <ol>
      <li>Introduction</li>
      <li>Créer une base de donnée</li>
      <li>Créer une table</li>
      <li>Ajouter des enregistrements</li>
      <li>Lire les enregistrements</li>
      <li>Conclusion</li>
    </ol>
    <h2>Introduction</h2>
    <p>
      Dans cette section, nous allons créer notre première
      <abbr class="db-tooltip tooltip" title="DataBase => Base de données">
        DB
      </abbr>
      "fat_cat_clinic" ayant pour but d'enregistrer le poids de votre animal de
      compagnie favoris <br />
      Nous verrons comment enregistrer et récupérer des données dans celle-ci et
      nous manipuleron pgAdmin pour la première fois <br />
      Notez bien que cette section ne fera qu'introduire les différents concepts
      de création, lecture, écriture... <br />
      Ceux-ci seront détaillés plus avant dans les prochaines sections
    </p>
    <h2>Créer une base de données</h2>
    <p>
      Lancez le programme pgAdmin et connectez vous. <br />
      À gauche se siture <strong>l'object explorer</strong> avec lequel vous
      pourrez facilement naviguer entre vos bases de données. <br />
      Naviguez dans celui-ci en ouvrant l'élément <strong>database</strong>.
      <br />
      Là, vous devriez voir une première base de données nommée
      <strong>postgre</strong> <br />
      À l'aide d'un clique droit sur cette dernière, ouvrez le menu contextuel
      et sélectionnez l'option <strong>Query Tool</strong> <br />
      Le query tool vous permet d'écrire vos
      <strong title="requêtes" class="tooltip">queries</strong>
      <strong>SQL</strong> et ainsi de communiquer avec votre système de gestion
      de base de données.
    </p>
    <p>
      Dans le query tool, entrez la ligne de code suivante pour créer votre
      première base de données
    </p>
    <code lang="sql">CREATE DATABASE fat_cat_clinic;</code>
    <p>
      Pour ceux qui parlent un peu anglais, vous comprendrez rapidement ce dont
      il est question ici. <br />
      Nous <i>créons</i> une <i>base de données</i> dont le nom est
      fat_cat_clinic. Le <kbd>;</kbd> signifiant la fin de la requête sql <br />
      Avant d'exécuter ce code, remarquez aussi que certains mots sont colorés.
      <br />
      Il s'agit de mots clés spécifique au langage <strong>SQL</strong> et sont
      dit <i>réservés</i> <br />
      Ainsi, on ne nommera pas de base de données <i>DATABASE</i> ou encore
      <i>CREATE</i>
    </p>
    <p>
      Concluez la création de votre base de donnée en utilisant la touche
      <kbd>F5</kbd> ou en utilisant le bouton d'exécusion de requête représenté
      par un petit triangle et situé juste au dessus du query tool.
    </p>
    <p>
      Faites un clique droit sur 'objet <strong>database</strong> de
      <strong>l'explorateur d'objet</strong> et sélectionnez l'option
      <strong>refresh</strong> pour voir s'affichez votre première base de
      données. <br />
      Félicitations
    </p>
    <h2>Crée une table</h2>
    <p>
      Pour fonctionner, votre
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr> va
      avoir besoin de <strong>tables</strong>.
    </p>
    <p>
      Une table est une <strong>collection de données structurées</strong>.
      C'est à dire, un tableau dans lequel ranger vos données selon une
      structure définie en amont.
    </p>
    <p>
      Dans une table, on pourra parler de <strong>colonnes</strong> qui seront
      nommées et définiront, entre autre, le <strong>type de donnée</strong>
      <br />
      et de <strong>rangées</strong> représentant chacunes un enregistrement de
      données au format précisé par les colonnes.
    </p>
    <p>
      Pour bien comprendre, nous allons créer une table dans la base de données
      fat_cat_clinic. Le but de cette table sera d'enregistrer régulièrement les
      pesées de notre animal. Nous allons donc nommer cette table
      <i>weight</i> et réfléchir eux données nécessaires pour garder un oeil à
      l'évolution du poids d'un chat.
    </p>
    <p>
      Un bon début sera de prendre note du poids et de la date de pesée. Nous
      aurons donc deux colonnes :
      <i>weight</i> (poids) et <i>date</i>.
    </p>
    <p>
      En plus de définir le nom de ces colonnes, il est nécessaire d'en définir
      le type. Pour le poids, nous utiliserons le type
      <strong>decimal</strong> permettant d'encoder des nombres décimaux en
      spécifiant la précision souhaitée. Pour la date, nous utiliserons le type
      <strong>date</strong> permettant d'encoder des... dates.
    </p>
    <p>
      Il existe et nous utiliserons d'autres types dans ce cours. Vous pouvez
      trouver une référence complète aux types disponibles en suivant
      <a href="https://www.postgresql.org/docs/current/datatype.html">
        ce lien vers la documentation officielle </a
      >.
    </p>
    <p>
      Pour l'instant, vous pouvez vous contentez de lire, comprendre, copier et
      éxecuter le code ci-dessous dans le <strong>query tool</strong> de
      <strong>pgAdmin</strong>
    </p>
    <code lang="sql">
      USE fat_cat_clinic; CREATE TABLE weight( weight decimal(3,1), date date )
    </code>
    <p>
      Détaillons ensemble ce code : <br />
      <code lang="sql">USE fat_cat_clinic;</code> permet de spécifier quelle
      base de données utiliser. Si vous ouvrez le
      <strong>query tool</strong> via la base de données ciblée, cette portion
      de code n'est pas nécessaire. Néanmoins, n'étant pas problèmatique et
      permettant de se prémunir d'éventuelles erreurs, il sera de bon goût de
      l'utiliser <br />
      <code lang="sql">CREATE TABLE weight(</code> permet, vous l'aurez compris,
      de créer une <strong>table</strong> dont le nom sera <i>weight</i> la
      parenthèse permet de spécifier ce que contiendra cette table <br />
      <code lang="sql">weight decimal(3,1)</code> permet de créer, dans la table
      weight, une colonne weight de type décimal. Beaucoup de déclaration de
      type demandent des informations complémentaires. Dans le cas de decimal,
      il est possible de spécifier entre parenthèses la précision (le nombre de
      chiffres dans le nombre) et l'échelle (le nombre de chiffres derrière la
      virgule) souhaitée. Ainsi, decimal(3,1) nous permettra d'encoder des poids
      en kg avec une précision à l'hectogramme et allant jusqu'à 99,9 kg. Nous
      devrions être bon pour nos chats
    </p>
    <h2>Ajouter des enregistrements</h2>
    <h2>Lire les enregistrements</h2>
  </section>
</template>
