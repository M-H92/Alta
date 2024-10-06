<template>
  <section>
    <h2>Battle box bluff</h2>
    <p>
      Marabout souhaite éditer une version en ligne de son jeu battle box bluff.
      <br />
      Les règles sont les suivantes : <br />
      Le jeu se joue avec un paquet de 200 cartes <br />
      Chaque carte contient une affirmation et 3 propositions de réponse<br />
      2 propositions sont fausses et la dernière est vraie <br />
      Tour à tour, les joueurs piochent une carte et lise la proposition ainsi
      qu'une réponse de leur choix <br />
      Les autres joueurs doivent deviner si oui ou non le joueur qui a tiré la
      carte a lu le bonne réponse ou a bluffé <br />
      Chaque carte dispose d'un nombre de point attribué aux joueurs qui ont
      devinés correctement<br />
      Chaque carte dispose aussi d'une anecdote liée à la question et d'une
      catégorie (culture générale, jeu vidéo, géographie,...)<br />
    </p>
    <h2>Factures</h2>
    <p>
      Un petit indépendant souhaite un programme pour gérer son entreprise<br />
      Une grande partie de son temps est dédié à la rédaction de devis et au
      suivi de sa facturation<br />
      Écrivez une base de données pour un programme qui permettra de créer un
      devis, une facture liée et de savoir si les factures sont payées ou pas<br />
      Voici un exemple de devis <br />
    </p>
    <div>
      Devis : 24092005 <br />
      Client : Thomas George <br />
      Total TTC : 178.70 € <br />
      Date : 24/09/20 <br />
      Accompte : 150 € <br />
      Reste à payer : 28.7 €
    </div>
    <table>
      <thead>
        <tr>
          <th>Objet</th>
          <th>Prix unitaire HTVA</th>
          <th>Unité</th>
          <th>Quantité</th>
          <th>Taux de tva</th>
          <th>Sous-total HTVA</th>
          <th>Commentaire</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Entretien poele</td>
          <td>50 €</td>
          <td>Heure</td>
          <td>2</td>
          <td>16%</td>
          <td>100 €</td>
          <td>Entretien et changement vitre</td>
        </tr>
        <tr>
          <td>Bois de chauffage</td>
          <td>6 €</td>
          <td>Stère</td>
          <td>10</td>
          <td>7%</td>
          <td>60 €</td>
          <td></td>
        </tr>
        <tr>
          <td>Vitre poele a bois</td>
          <td>50 €</td>
          <td>Pièce</td>
          <td>1</td>
          <td>17%</td>
          <td>50 €</td>
          <td>En stock</td>
        </tr>
      </tbody>
    </table>
    <h2>Gestion de stock</h2>
    <p>
      Le même entrepreneur a vu sa part de revenu entre la vente et le service
      évoluer de telle sorte qu'il fasse maintenant beaucoup plus d'achat /
      vente que de services <br />
      Par conséquent, la gestion de son stock est devenue plus complexe <br />
      Modifier la base de donnée pour implémenter une gestion de stock
    </p>
    <h2>Échec</h2>
    <p>
      Un éditeur de jeu de plateau souhaite se lancer dans le développement
      d'une plateforme en ligne de jeu d'Échec
      <br />
      Non seulement, ils souhaitent pouvoir enregistrer les joueurs, leur elo et
      leur adresse email<br />
      Mais en plus, ils souhaitent garder une trace des différentes parties
      jouées <br />
      Aux échecs, une partie est une succession de coups avec une notation dont
      les règles sont la suivante <br />
      On commence par un coup blanc suivi d'un coup noir tout deux séparés par
      une virugule <br />
      Une paire de coup (blanc et noir) est suivi d'un retour à la ligne
      <br />
      Une initiale désigne la pièce jouée sauf si la pièce jouée est évident
      (une unique pièce est capable de faire ce déplacement)<br />
      Un caractère <b>x</b> est ajouté si le coup résulte en une prise de pièce
      adverse <br />
      La case d'arrivée de la pièce jouée est noté avec une lettre allant de a à
      h et un nombre de 1 à 8<br />
      Si le coup joué met le roi adverse en échec, un caractère <b>+</b> est
      ajouté à la fin du coup <br />
      Si le coup joué met le roi adverse en échec et mat, un caractère
      <b>#</b> est ajouté. Accessoirement, la partie est finie<br />
      Un coup brillant est parfois noté en ajoutant un caractère <b>!</b> voir
      <b>!!</b> dans les cas les plus rares<br />
      Un coup spécial, le roque, est noté avec la suite de caractères
      <b>O-O</b> ou <b>O-O-O</b> selon qu'il s'agisse d'un petit roque ou d'un
      grand roque<br />
      Les paires de coups sont numérotés à partir de 1 et incrémentent d'une
      unité à la fois dans l'ordre chronologique de la partie<br />
      Un exemple de suite de coups pourrait être le suivant <br />
      4. e5,Nfd7 <br />
      5. f4,c5 <br />
      6. Nf3,Nc6 <br />
      Les différentes pièces sont représentés par : <br />
      Le roi (King) - K <br />
      La dame (Queen) - Q <br />
      La tour (Rook) - R <br />
      Le fou (Bishop) - B <br />
      Le cavalier (kNight) - N (K étant déjà utilisé pour le roi) <br />
      Le pion (pawn) - N/A. Le pion n'est jamais représenté par son initiale
      <br />
      Le pion n'étant jamais représenté par son initiale, un coup ambigu joué
      par un pion sera noté avec la colonne de départ du pion plutôt que son
      initiale : <br />
      exf6 => le pion e5 prends f6
    </p>
  </section>
</template>
