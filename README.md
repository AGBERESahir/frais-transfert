# frais-transfert

Compare ce que ton proche **reçoit réellement** lors d'un transfert d'argent, en comptant les frais *et* le taux de change.

**Démo : https://agberesahir.github.io/frais-transfert/**

Les frais affichés par les services de transfert ne sont qu'une partie du coût : le taux de change appliqué cache souvent le reste. Un service « sans frais » peut coûter plus cher qu'un service avec frais mais meilleur taux. Cette page fait le calcul à ta place, à partir des tarifs que tu relèves toi-même.

- Un seul fichier HTML, aucune installation, aucun compte.
- Fonctionne hors ligne une fois la page ouverte, sur téléphone comme sur ordinateur.
- Respecte le mode sombre et la réduction des animations de ton appareil.

## Comment l'utiliser

1. Choisis ce que tu veux savoir : **comparer pour un montant que j'envoie**, ou **combien envoyer pour que mon proche reçoive un montant précis** (voir plus bas).
2. Indique le montant et les deux **devises** (par exemple XOF et EUR).
3. Indique le **taux de référence** : combien vaut 1 unité envoyée dans la devise reçue. Relève-le sur une source neutre (banque centrale, site de taux moyens), pas chez le service de transfert.
4. Indique la **date à laquelle tu as relevé les tarifs**. Au-delà de 3 jours, la page t'avertit de les revérifier.
5. Pour chaque service, saisis ses **frais fixes**, ses **frais en %** et le **taux qu'il applique** vraiment.
6. Lis le classement : le service le plus avantageux est en haut, marqué d'une bordure verte.

Utilise « Ajouter un service » pour comparer plus de deux offres, et « Retirer » pour en enlever.

### Les deux modes

| Mode | Tu donnes | La page te dit |
|---|---|---|
| Comparer pour un montant envoyé | Le montant que tu envoies | Ce que ton proche reçoit chez chaque service |
| Combien envoyer | Le montant que ton proche doit recevoir (loyer, facture, scolarité…) | Combien tu dois envoyer chez chaque service |

### Partager la comparaison

- **Copier le lien** : l'adresse contient toute ta comparaison (montant, devises, services). Envoie-la à un proche : en l'ouvrant, il voit exactement les mêmes chiffres. Rien n'est stocké sur un serveur.
- **Copier le résumé** : un texte court prêt à coller dans WhatsApp ou un SMS.

## Comment c'est calculé

```text
reçu       = (montant − frais fixes − montant × frais % / 100) × taux appliqué
coût réel  = montant − reçu / taux de référence

mode « combien envoyer » :
envoyé     = (montant à recevoir / taux appliqué + frais fixes) / (1 − frais % / 100)
```

Le **coût réel** est exprimé dans la devise envoyée, avec son pourcentage du montant : c'est ce que tu perds en tout, frais et écart de taux confondus, par rapport au taux de référence.

### Exemple

Envoi de 100 000 XOF, taux de référence `0,00152` (valeurs pré-remplies dans la page) :

| Service | Frais fixes | Frais % | Taux appliqué | Ton proche reçoit | Coût réel |
|---|---|---|---|---|---|
| Service A | 1 000 | 1,5 % | 0,00148 | 144,30 EUR | 5 065,79 XOF (5,1 %) |
| Service B | 0 | 3 % | 0,00151 | 146,47 EUR | 3 638,16 XOF (3,6 %) |

Le service B affiche des frais deux fois plus élevés en pourcentage, mais il est **plus avantageux de 2,17 EUR** grâce à son meilleur taux.

## Tes données

- Tout ce que tu saisis (mode, montants, devises, taux, services) est enregistré **dans ton navigateur** (`localStorage`) pour le retrouver à la prochaine visite. Rien n'est envoyé à un serveur.
- Un lien partagé **remplace** ce qui est affiché, mais ne modifie ta sauvegarde que si tu changes ensuite un champ.
- Les données d'un lien sont revérifiées à l'ouverture : un lien abîmé ou piégé est ignoré et la page revient à ses valeurs par défaut.
- Les deux services pré-remplis sont des **exemples** : remplace-les par les tarifs réels.
- Vider les données du navigateur efface la liste.
- Seule la police Atkinson Hyperlegible est chargée depuis Google Fonts. Si elle ne se charge pas, la page utilise la police système.

## Limites

- La page ne va chercher **aucun taux ni aucun tarif** : tout est saisi à la main. C'est voulu, pour ne dépendre d'aucun service et ne pas afficher de chiffres périmés.
- Les frais sont modélisés comme « un montant fixe + un pourcentage ». Les barèmes par tranche ou les frais côté destinataire ne sont pas gérés.
- Un service dont les frais atteignent 100 % ou dont le taux est nul est signalé comme incohérent et classé en dernier.
- Le lien partagé contient tes chiffres dans l'adresse : ne le publie pas si tu ne veux pas les montrer.
- Le résultat n'est aussi bon que les chiffres saisis : vérifie les tarifs sur le service juste avant d'envoyer.
- Les délais, la fiabilité et les modes de retrait ne sont pas comparés.

## Utiliser en local

```bash
git clone https://github.com/AGBERESahir/frais-transfert.git
cd frais-transfert
# puis ouvre index.html dans ton navigateur
```

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | La page et sa logique (HTML, CSS propre à la page, JavaScript). |
| `shared.css` | Styles communs avec [documents-types](https://github.com/AGBERESahir/documents-types) et [rappels-echeances](https://github.com/AGBERESahir/rappels-echeances). |

## Licence

MIT, voir [LICENSE](LICENSE).
