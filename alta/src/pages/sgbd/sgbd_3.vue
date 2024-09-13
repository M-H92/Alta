<template>
  <section>
    <h2>Contraintes</h2>
    <p>
      Quand nous avions ajouté le nom de l'animal à notre table, nous avions eu
      un problème de <i>null</i>. <br />
      Petit rappel, null représente, pour un colonne d'un record, qu'il n'y a
      pas de données
    </p>
    <p>
      Ceci nous avais contraint à modifier nos données via une requête
      <i>UPDATE</i> avec l'utilisation d'un <i>WHERE</i> et, heureusement, la
      différence de poids entre mon chat et celui de ma belle soeur était telle
      qu'une clause where sur le poids de nos animaux avait suffit à discerner
      nos animaux
    </p>
    <p>
      Néanmoins, à l'avenir, avec plus de chats ou de pesées, ça pourrait ne
      plus suffire.
    </p>
    <p>
      Nous allons donc nous prémunire de ce problème avec une
      <strong>constraint</strong>
    </p>
    <p>
      Une <i>constraint</i> est, comme son nom l'indique, une contrainte que
      l'on peut appliquer, par exemple, sur notre colonne <i>cat</i> pour
      interdire les valeurs nulles. Appliquons la avec le code suivant :
    </p>
    <code> ALTER TABLE weight ALTER COLUMN cat SET NO NULL; </code>
    <p>
      Pas de surprise ici. Les différents mot-clés sont presque tous connus
      <br />
      Nous <i>alterons</i> la <i>table</i> <i>weight</i> pour laquelle nous
      <i>alterons</i> la <i>colonne</i> <i>cat</i> <br />
      Pour cette colonne, nous spécifions qu'elle ne peut pas contenir la valeur
      <i>null</i> avec <strong>SET NO NULL</strong>
    </p>
    <p>
      Tant que nous y somme, posons nous la question : est-ce qu'une pesée sans
      poids peut avoir du sens? quid d'une pesée non datée? Ajoutons aussi les
      contraintes <i>NO NULL</i> pour ces deux colonnes
    </p>
    <p>
      Vous avez peut-être essayé de mettre la contrainte <i>NO NULL</i> alors
      que votre colonne contenait déjà des valeurs nulles. <br />
      Non? <br />
      Essayez-donc pour voir le résultat <br />
      Essayez aussi d'insérer des valeurs nulles maintenant que les contraintes
      sont appliquées
    </p>
    <h2>Problème de poids</h2>
    <p>
      Pour profiter des capacités de notre base de données à traiter la donnée
      lors de la récupération, nous allons ajouter quelques informations de
      <strong>référence</strong> dans notre table.
    </p>
    <p>En vrac :</p>
    <ul>
      <li>Le poids moyen vers lequel devrait tendre notre chat</li>
      <li>La race de notre chat</li>
      <li>Son sexe</li>
      <li>Son âge</li>
      <li>S'il est stérilisé</li>
    </ul>
    <p>
      Si nous ajoutons toutes ces informations notre table weight, nous nous
      retrouvons avec ce genre de résultat
    </p>
    <table>
      <thead>
        <tr>
          <th>weight</th>
          <th>date</th>
          <th>cat</th>
          <th>ideal_weight</th>
          <th>race</th>
          <th>is_male</th>
          <th>age</th>
          <th>neutered</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>3.5</td>
          <td>'2024-02-02'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.6</td>
          <td>'2024-03-04'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.5</td>
          <td>'2024-04-02'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.6</td>
          <td>'2024-05-10'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
        <tr>
          <td>3.7</td>
          <td>'2024-06-08'</td>
          <td>'Monza'</td>
          <td>6.5</td>
          <td>'Persan'</td>
          <td>true</td>
          <td>7</td>
          <td>true</td>
        </tr>
      </tbody>
    </table>
    <p>
      prennez un peu de temps pour regarder ces données et remarquons quelque
      chose...
    </p>
    <p>
      Nous avons beaucoup de <strong>répétitions</strong> et cela est un
      problème.
    </p>
    <p>
      Tout d'abord, nous devons maintenant ajouter ces informations lors de
      l'insertion de chaque record dans notre table <i>weight</i>. <br />
      Non seulement, cela va nous prendre plus de temps, mais en plus, c'est une
      source d'erreur potentielle ! <br />
      Que faire quand mon chat sera une fois de race <i>persan</i> et une autre
      de race <i>maine coon</i> ? Quelle information conserver ?
    </p>
    <p>
      Ensuite, nous augmentons considérablement le poids de chaque record pour
      des informations qui ne sont pas variables entre deux pesées (sauf pour
      l'âge et s'il est stérilisé. Nous reviendrons là-dessus plus tards) <br />
      Effectivement, nous passons d'un record avec 3 champs assez léger à un
      record de 8 champs ! <br />
      Et bien que ceux-ci ne soient pas individuellement trop lourd, le poids de
      ceux-ci se fera sentir lors de l'accumulation d'un plus grand nombre de
      records.
    </p>
    <p>
      Réflechissez a de potentielles solutions à ce problème de répétition de
      données avant de lire la suite. <br />
      Comment pourriez-vous résoudre ce problème si vous preniez des notes
      papier plutôt qu'en utilisant une base de données?
    </p>
    <h2>Relations</h2>
    <p>
      Je vous propose de résoudre ce problème en vous présentant le principe de
      relations dans une base de données
    </p>
    <p>
      Certains l'auront déjà remarqué ou entendu : on parle parfois de base de
      données <strong> relationnelles </strong>. <br />
      L'idée est simple : créer plusieurs tables et établir des
      <i>relations</i> entre ces tables pour pouvoir liers les données de l'une
      et de l'autre
    </p>
    <p>
      Dans notre cas, nous pourrions séparer nos données entre celles qui sont
      en rapport direct avec notre chat en soi (nom, race, sexe, age, poids
      idéal, stérilisé ) et celles qui ont un rapport avec les différentes
      pesées de nos chats (poids, date et nom) <br />
      Nous aurions donc les deux tables suivantes :
    </p>
    <p>weight</p>
    <ul>
      <li>weight</li>
      <li>date</li>
      <li>name</li>
    </ul>
    <p>cat</p>
    <ul>
      <li>name</li>
      <li>race</li>
      <li>is_male</li>
      <li>age</li>
      <li>ideal_weight</li>
      <li>neutered</li>
    </ul>
    <p>
      Vous avez remarqué quelque chose? <br />
      C'est ça, la colonne <i>name</i> est dupliquée dans les deux tables car
      une pesée est liée à un chat, tout comme les informations générales !
      <br />
      C'est normal gardez bien ça en tête car nous allons en profiter par après.
      <br />
      En attendant, mettons en place ces deux tables avec le code suivant :
    </p>
    <pre>
      CREATE TABLE weighting(
        name varchar(32),
        date date,
        weight numeric(3,1)
      );

      CREATE TABLE cat(
        name varchar(32),
        race varchar(32),
        is_male boolean,
        age int,
        ideal_weight numeric(3,1),
        neutered boolean
      )
    </pre>
    <p>Et ajoutons quelques données</p>
    <pre>
      INSERT INTO weighting (weight, date, name) 
      VALUES (3.6, '2024-08-03', 'Monza')
        ,(3.7, '2024-07-06', 'Monza') 
        ,(3.5, '2024-06-01', 'Monza') 
        ,(3.6, '2024-05-04', 'Monza') 
        ,(3.4, '2024-04-06', 'Monza') 
        ,(3.4, '2024-03-02', 'Monza') 
        ,(3.5, '2024-02-03', 'Monza')
        ,(7.5, '2024-06-03', 'Plume') 
        ,(7.6, '2024-05-04', 'Plume') 
        ,(7.5, '2024-04-05', 'Plume') 
        ,(7.4, '2024-03-02', 'Plume');
      
      INSERT INTO cat (name, race, is_male, age, ideal_weight, neutered)
      VALUES ('Monza', 'Persan', true, 7, 6.5, true)
        ,('Plume', 'Maine coon', false, 5, 6, true)
    </pre>
    <p>
      Vous devriez être en mesure d'identifier tout les éléments de ces deux
      requêtes, bien que certains types soient utilisés ici pour la première
      fois. <br />
      Si des questions persistaient, n'hésitez pas à consulter les chapitres
      précédents ou à faire une recherche rapide sur internet avant de passer à
      la prochaine section
    </p>
    <h2>Jointures (introduction)</h2>
    <p>
      Revenons maintenant à cette donnée dupliquée <br />
      Vous vous souvenez, nous avions parlé plus tôt de relations entre les
      tables... <br />
      Et bien c'est cette donnée dupliquée qui va nous permettre de créer et
      manipuler ces relations. <br />
      Nous pouvons maintenant mettre <i>en relation</i> les données
      <i>name</i> des tables <i>weighting</i> et <i>cat</i> (il ne s'agit pas
      ici de la véritable définition d'une relation en base de données. Nous
      reviendrons sur celle-ci plus tard) <br />
    </p>
    <p>
      Maintenant, si nous voulons récupérer une pesée ainsi que le poids idéal
      de notre chat, nous n'avons "qu'à" récupérer les données présentes dans la
      table <i>weighting</i> pour 'Monza'... Et, toujours pour 'Monza', les
      données de la table <i>cat</i>... En même temps... <br />
      Pas de panique, c'est nettement moins compliqué que ça en à l'air.
      Analysez plutôt le code ci-dessous :
    </p>
    <pre>
      SELECT cat.name, cat.ideal_weight, weighting.weight, weighting.date
      FROM cat
      JOIN weighting ON cat.name = weighting.name
      ORDER BY weighting.date DESC;
    </pre>
    <p>
      Tout d'abord, notons une différence sur l'écriture des noms de colonne.
      <br />
      Elles sont nommées avec le nom de la table, suivie d'un point et du nom de
      colonne. <br />
      Ceci permet, lors de la manipulation de plusieurs tables, de ne pas se
      tromper sur la provenance des données. <br />
      Cette nomenclature était d'ailleurs déjà faisable avec une unique table,
      mais a tendance à rendre plus lourde la lecture et a donc été évitée.
      <br />
      À l'inverse, la nomenclature sans le nom de table est tout à fait
      envisageable pour les colonnes comme ideal_weight pour lesquelles la
      provenance ne fait aucun doute. Mais il est en général avisé de précéder
      chaque colonne de sa table lors de jointures pour se faciliter la tâche à
      la lecture.
    </p>
    <p>
      Ensuite, regardons le nouveau mot clé en deux partie <br />
      <code>JOIN table ON critère</code> permet de <i>joindre</i> une table à la
      table courante sur base d'un critère. De faire une
      <strong>liaison</strong>, une <strong>jointure</strong>. Ici, le critère
      est une simple égalité entre les valeurs des colonnes <i>name</i> des
      tables <i>cat</i> et <i>weighting</i>
    </p>
    <p>
      Pour le plaisir de la lecture, réduisont un peu la taille de cette requête
      en utilisant une notion vue précédement, les alias, mais sur les tables.
    </p>
    <pre>
      SELECT c.name, c.ideal_weight, w.weight, w.date 
      FROM cat AS c 
      JOIN weighting as w on c.name = w.name
      ORDER BY w.date DESC;
    </pre>
    <p>
      Encore mieux, nous prenoms toutes les colonnes de la table
      <i>weighting</i>. Essayons ceci :
    </p>
    <pre>
      SELECT w.*, c.ideal_weight 
      FROM cat as c 
      JOIN weighting as w on c.name = w.name 
      ORDER BY w.date DESC;
    </pre>
    <p>
      Il est même possible de faire une requête de ce genre
      <code>SELECT w.*, c.*</code>. Je vous laisse imaginer le résultat
    </p>
    <p>Avant de passez à la section suivante, je vous propose deux exercices</p>
    <p>
      D'abord, essayez de modifier encore la base de données en séparant les
      données dans une troisième table. <br />
      Réfléchissez bien à la manière de séparer les données de façon logique,
      et, si vous avez besoin d'un indice, demandez-vous ce qu'il se passerait
      si nous ajoutions un autre chat persan ou maine coon
    </p>
    <p>
      Ensuite, maintenant cette séparation faite, essayez de récupérer les
      informations en faisant une double jointure ! (si, si, c'est faisable)
      <br />
      Vous devrez certainement faire une recherche internet pour trouver une
      solution. Mais n'hésitez pas à tester ce qu'il vous semblerait logique
      avant ça. Quitte à vous tromper.
    </p>
    <!-- <h2>Clé primaires</h2>
    <h2>Clé étrangères</h2>
    <h2>Requêtes imbriquées (introductions)</h2>
    <h2>Tables de liaison</h2> -->
  </section>
</template>
