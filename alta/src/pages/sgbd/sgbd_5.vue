<template>
  <section>
    <h2>Cardinalité</h2>
    <p>
      Notre base de données commence à s'étoffer. <br />
      Nous diposons maintenant de 3 tables : cat, weighting, reference <br />
      Grâce à ces tables, nous avons maintenant la possibilité de suivre le
      poids de plusieurs chats et de les comparer à des valeurs de références en
      utilisant des jointures.
      <br />
      Tout ça commence à ressembler à une véritable base de données utilisable
      dans un vrai programme de gestion de son animal <br />
      Comme je souhaite monitorer d'autres données relatives à mon chat,
      profitons en pour améliorer ce qui a été fait plutôt que de rechercher une
      solution séparée.
    </p>
    <p>
      Mon chat se fait vacciner pour plusieurs maladies et ces vaccins disposent
      parfois de rappel à administrer à des dates différentes et variées <br />
      En ajoutant ces informations dans la
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>, je
      pourrais avoir toutes mes données au même endroit. <br />
      Réflechissons à comment mettre ces vaccins dans notre
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
    </p>
    <p>Chaque vaccin dispose des informations suivantes :</p>
    <ul>
      <li>Un nom</li>
      <li>
        Une date de première administration (l'âge de l'animal à partir duquel
        il peut être administré)
      </li>
      <li>Un délais de rappel</li>
      <li>S'il est obligatoire ou conseillé</li>
      <li>Et enfin une maladie liée</li>
    </ul>
    <p>
      Concernant ce dernier point, nous n'allons pas étendre cet aspect de la
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      <br />
      Notre but est de récolter les données de nos chats, pas de faire une
      <abbr class="db-tooltip" title="DataBase => Base de données">DB</abbr>
      exhaustive sur les différentes maladies félines
    </p>
    <p>
      Réflechissez à la manière d'intégrer ces informations dans notre base de
      données...
    </p>
    <p>
      En se basant sur ce qui a déjà été vu au cours, nous pourrions avoir envie
      d'ajouter une nouvelle table dédiée ou simplement des colonnes dans une
      table existante
      <br />
      Il me semble néanmoins compliqué de justifié l'ajout des données des
      différents vaccins aux trois tables déjà en place. <br />
      Si nous voulons créer une nouvelle table vaccin, nous allons rencontrer un
      problème que nous avons déjà eu par le passé. <br />
      Comment lier un vaccin à un chat? <br />
      Nous pourrions ajouter l'id d'un chat au vaccin... <br />
      Mais nous allons alors répéter des informations relatives au vaccin à
      chaque fois qu'un chat est inoculé <br />
      Si nous faisons l'inverse, nous allons limiter notre chat à un unique
      vaccin...
    </p>
    <p>
      La solution sera d'utiliser une table dite <i>de liaison</i> ou encore
      <i>intermédiaire</i>. <br />
      Le but de ces tables est de lier des données multiples entre 2 autres
      tables ou plus. <br />
      Pour se faire, créons une table de vaccin et une table de liaison entre
      cat et vaccin
    </p>
    <pre>
        CREATE TABLE  vaccine(
            name varchar(32) PRIMARY KEY,
            description varchar(420),
            first_inoculation_week int,
            mandatory boolean,
            illness varchar(32),
            years_before_booster integer
        )

        CREATE TABLE cat_vaccine(
            vaccine_name varchar(32),
            cat_name varchar(32),
            inoculation date,
            PRIMARY KEY(vaccine_name, cat_name),
            CONSTRAINT fk_vaccine 
                FOREIGN KEY(vaccine_name) 
                REFERENCES vaccine(name),
            CONSTRAINT fk_cat 
                FOREIGN KEY(cat_name) 
                REFERENCES cat(name)
        )
    </pre>
  </section>
</template>
