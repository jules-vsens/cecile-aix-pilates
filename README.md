# Cécile Aix Pilates

Site vitrine des cours de Pilates de Cécile Magro (kiné diplômée d'État en 2020 et danseuse) à Aix-en-Provence.

C'est un site statique d'une page : du HTML et du CSS, sans JavaScript, sans framework et sans étape de build. Pour le modifier, il suffit d'éditer les fichiers et de les pousser sur GitHub.

- **Dépôt** : https://github.com/jules-vsens/cecile-aix-pilates
- **Aperçu GitHub Pages** : https://jules-vsens.github.io/cecile-aix-pilates/
- **Domaine prévu** : https://cecileaixpilates.fr (pas encore acheté)

## Fichiers

| Fichier | Rôle |
|---|---|
| `index.html` | Tout le site : contenu, styles (`<style>` dans le `<head>`) et données Google (bloc JSON-LD) |
| `mentions-legales.html` | Mentions légales, non indexées par Google |
| `robots.txt`, `sitemap.xml` | Référencement ; ils pointent vers `cecileaixpilates.fr` |
| `images/` | Photos et logo, voir `images/LISEZ-MOI.txt` |
| `.gitignore` | Garde hors du dépôt les notes internes `mise-en-ligne.md` et `guide-fiche-google.md` |

## Voir le site en local

Ouvre `index.html` dans un navigateur, c'est tout.

## Modifications courantes

Toutes les modifications se font dans `index.html`. Utilise Ctrl+F pour trouver le bon endroit.

### Changer un prix ou une formule
Cherche `class="formules"`. Il y a trois cartes : À l'unité, Abonnement (la carte `vedette`, mise en avant) et Carte 10 séances. Quand tu changes un prix, mets aussi à jour :
- le prix par séance (`par-seance`) et le badge d'économie (`economie`) de la carte ;
- les conditions (`Conditions de l'abonnement et de la carte`) ;
- la FAQ si elle en parle ;
- `"priceRange"` dans le bloc JSON-LD en haut du fichier.

### Ajouter un créneau
- La carte du créneau : cherche `class="creneau card"`.
- Les messages de réservation WhatsApp et SMS disent « du mardi 9h » : cherche `mardi%209h`.
- Les horaires pour Google : `openingHoursSpecification` dans le JSON-LD.
- Les mentions « Mardi 9h » dans la pastille du haut (`class="dispo"`) et la barre mobile (`barre-places`).

### Mettre les photos et le logo
Dépose les images dans `images/` (noms et formats conseillés dans `images/LISEZ-MOI.txt`, 300 Ko max chacune), puis :
- remplace chaque `<div class="photo-ph">…</div>` par
  `<img src="images/nom.jpg" alt="description" loading="lazy" style="width:100%;height:100%;object-fit:cover">` ;
- remplace `<span class="logo-ph" …>logo</span>` par
  `<img src="images/logo.svg" alt="" width="36" height="36">` ;
- ajoute `images/og.jpg` (1200 × 630), l'image qui s'affiche quand on partage le lien.

### Réactiver les avis
La section est en commentaire : cherche `AVIS`. Ne la réactive **qu'avec de vrais avis d'élèves de Pilates**, jamais des avis inventés ni des avis de patients du cabinet.

## Design

Tous les réglages sont des variables CSS en haut du `<style>` de `index.html`.

- **Polices** :
  - Poppins en 3 graisses seulement : 300 pour les titres, 400 pour le texte, 500 pour les boutons, labels et prix. N'en ajoute pas d'autre.
  - Parisienne (script) seulement en accent : le mot « danseuse », les petites accroches au-dessus des titres, la signature. Jamais pour un paragraphe.
- **Palette pastel** : `--sable` (fond), `--lin`, `--sauge-pale`, `--sauge`, `--sauge-fonce` (boutons), `--poudre`, `--encre`.
- **Composants** inspirés de [coss ui](https://coss.com/ui) :
  - `.btn` avec ses variantes `.btn-plein`, `.btn-ligne` et `.btn-lg` ;
  - `.card`, `.badge` ;
  - l'accordéon (`<details>`).
- **Règles UI** : cibles tactiles de 44px minimum, chiffres alignés (`tabular-nums`), rayons d'angle cohérents (`--r-sm`, `--r`, `--r-lg`, `--r-xl`), animations coupées si le visiteur a demandé moins d'animations sur son appareil.

## Règles de contenu

- On **tutoie** le visiteur, avec un ton bienveillant.
- Des **prix ronds**.
- **Aucun faux avis** et **aucune fausse rareté** : « Places limitées à 10 » est toujours vrai, un compteur de places ne l'est pas s'il n'est pas tenu à jour.
- **Aucune mention d'un public senior.**
- On rappelle toujours que le cours **n'est pas un acte de kinésithérapie** (FAQ et mentions légales).

## Publier une modification

```bash
git add .
git commit -m "Nouveau créneau jeudi 19h"
git push
```

GitHub Pages met le site à jour en 1 à 2 minutes.

**Première activation**, à faire une seule fois : **Settings → Pages → Source : Deploy from a branch → `main` / `(root)` → Save**. Avec un compte gratuit, le dépôt doit être public.

## Avant la vraie mise en ligne

- [ ] Photos, logo et `images/og.jpg` ajoutés
- [ ] SIRET, adresse et e-mail complétés dans `mentions-legales.html`
- [ ] Texte « Moi, c'est Cécile » relu et validé par Cécile
- [ ] Communication validée par l'Ordre des masseurs-kinésithérapeutes (conseil départemental 13)
- [ ] Mention « TVA non applicable, article 293 B du CGI » confirmée (franchise de TVA) ou retirée
- [ ] Périodes de fermeture et règle de rattrapage de l'abonnement validées
- [ ] Compte Instagram à jour : le site pointe encore vers `@kinaixpilates`
- [ ] Domaine `cecileaixpilates.fr` acheté et branché. Si l'hébergeur change (Cloudflare Pages par exemple), mettre à jour la partie « Hébergement » des mentions légales.
