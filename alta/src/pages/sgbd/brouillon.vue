<!-- <h2>Pokemons</h2>
    <p>
      Un pokemon est une créature de jeu vidéo dont le but est de faire
      combattre une équipe de 1 à 6 pokemons contre l'équipe d'un joueur adverse
      <br />
      Les pokémons disposent d'un nom, d'un ou deux "types" parmis 15 et de 6
      statistiques représentées par des nombres entiers ne dépassant pas 999.
      <br />
      Ces 6 statistiques sont : l'attaque, la défense, l'attaque spéciale, la
      défense spéciale, les points de vie et la vitesse <br />
      Le code suivant permet de créer une base de données permettant de créer
      des "équipes" de pokemon<br />
      Sur base de ces données, trouver : <br />
      Quel pokemon dispose du plus grand nombre de points de vie <br />
      Quel pokemon dispose du plus petit nombre de points de vie <br />
      Quel pokémon dispose des plus hautes défenses (combinées) <br />
      Lister les 10 pokemons avec la plus haute vitesse par ordre décroissant
      <br />
      Lister le pokemon de type "feu" avec la plus haute vitesse <br />
      Montrer les statistiques des 10 pokemons avec le total de statistiques le
      plus élevé <br />
      Parmis les différentes équipes, laquelle dispose, tout pokemon de l'équipe
      combinés, du plus d'attaque <br />
      Quels pokemons sont repris dans les équipes par ordre décroissant
      d'occurence <br />
    </p>
    <pre>
      CREATE DATABASE pokemon;
      USE pokemon;
      CREATE TABLE types(
        id serial,
        nom varchar(8)
      )
      CREATE TABLE pokemons(
        id integer PRIMARY KEY,
        nom varchar(16) NOT NULL,
        id_type_principal integer NOT NULL REFERENCES types (id),
        id_type_secondaire integer REFERENCES types (id),
        attaque integer NOT NULL CHECK (attaque > 0),
        defense integer NOT NULL CHECK (defense > 0),
        attaque_speciale integer NOT NULL CHECK (attaque_speciale > 0),
        defense_speciale integer NOT NULL CHECK (defense_speciale > 0),
        vitesse integer NOT NULL CHECK (vitesse > 0),
        points_de_vie integer NOT NULL CHECK (points_de_vie > 0),
      )
      CREATE TABLES teams(
        id serial,
        nom varchar(16),
        id_pokemon_1 integer NOT NULL REFERENCES pokemons (id),
        id_pokemon_2 integer NOT NULL REFERENCES pokemons (id),
        id_pokemon_3 integer NOT NULL REFERENCES pokemons (id),
        id_pokemon_4 integer NOT NULL REFERENCES pokemons (id),
        id_pokemon_5 integer NOT NULL REFERENCES pokemons (id),
        id_pokemon_6 integer NOT NULL REFERENCES pokemons (id),
      )
      INSERT INTO types (nom)
      VALUES (Acier),
        (Combat),
        (Insecte),
        (Normal),
        (Poison),
        (Roche),
        (Sol),
        (Spectre),
        (Vol),  
        (Dragon), 
        (Eau), 
        (Electrik), 
        (Feu), 
        (Glace), 
        (Plante), 
        (Psy), 
        (Ténèbres)
    </pre> -->
