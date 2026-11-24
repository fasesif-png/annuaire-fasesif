# Annuaire des présidents FASESIF

Application web de l'annuaire des présidents des associations membres de la FASESIF.
Une seule adresse fonctionne sur ordinateur, Android et iPhone, sans abonnement ni compte pour les présidents.

- **Tout est en ligne et gratuit** : l'application est hébergée par GitHub Pages, les données par Google Sheets. Rien ne tourne sur un ordinateur personnel.
- **Tout appartient à la FASESIF** : le tableur, le service et le dépôt GitHub sont créés avec le compte de la FASESIF. Pour passer la main au bureau suivant, il suffit de transmettre les identifiants de ce compte.
- **Chaque président** reçoit un code d'accès personnel. Ses modifications partent « en attente ».
- **Le coordinateur** valide ou refuse chaque proposition, modifie directement n'importe quelle fiche, ajoute ou supprime des associations et gère les codes. Il reçoit un e-mail à chaque fiche envoyée.

Adresse : **https://fasesif-png.github.io/annuaire-fasesif/** (compte GitHub `fasesif-png`).

---

## Étape 0 : se connecter avec le compte de la FASESIF

- Dans Chrome ou Edge, ouvrez une **fenêtre de navigation privée** (Ctrl+Maj+N) et connectez-vous à Google avec le **compte de la FASESIF**. Ainsi, le tableur et le service ne seront pas créés sur un compte personnel.
- Faites toutes les étapes suivantes dans cette fenêtre.

## Étape 1 : créer le tableur Google (5 minutes)

1. Ouvrez **https://sheets.new** et nommez le tableur `Annuaire FASESIF`.
2. Menu **Extensions > Apps Script**.
3. Ouvrez le fichier `google-apps-script/Code.gs` avec le Bloc-notes (clic droit > Ouvrir avec > Bloc-notes), faites Ctrl+A puis Ctrl+C.
4. Dans Apps Script, faites Ctrl+A dans le code affiché, puis Ctrl+V. Cliquez sur la **disquette** pour enregistrer.
5. Dans la liste à droite de « Déboguer », choisissez **installer**, puis **▶ Exécuter**.
   - Cliquez sur **Examiner les autorisations**, choisissez le compte de la FASESIF.
   - Sur « Google n'a pas validé cette application », cliquez sur **Paramètres avancés > Accéder à … (non sécurisé) > Autoriser**. C'est normal : c'est votre propre script.
6. Revenez au tableur : 5 onglets sont créés. **Le code coordinateur est à la ligne 2 de l'onglet Accès.** Gardez-le pour le bureau.

## Étape 2 : activer le service (3 minutes)

1. Dans Apps Script : **Déployer > Nouveau déploiement > roue dentée > Application Web**.
2. **Exécuter en tant que** : Moi. **Qui a accès** : **Tout le monde** (pas « Tout le monde disposant d'un compte Google »).
3. **Déployer**, puis copiez l'**URL de l'application Web**, qui se termine par `/exec`.

## Étape 3 : créer le compte GitHub de la FASESIF et mettre l'annuaire en ligne (10 minutes)

1. Toujours dans la fenêtre privée, allez sur **https://github.com/signup** et créez un compte gratuit **avec l'adresse e-mail de la FASESIF**. Nom d'utilisateur : `fasesif-png`.
2. Une fois connecté : **+ > New repository**. Nom : `annuaire-fasesif`, cochez **Public**, puis **Create repository**.
3. Cliquez sur **uploading an existing file** et glissez ces éléments du dossier `annuaire-github` : `index.html`, `config.js`, `manifest.webmanifest`, `LISEZ-MOI.md` et le dossier `icons`. **Ne déposez pas** le dossier `google-apps-script` : il ne sert que dans Apps Script. Cliquez sur **Commit changes**.
4. Cliquez sur **config.js**, puis sur le **crayon**. Collez l'URL de l'étape 2 entre les guillemets de `apiUrl: ""`, puis **Commit changes**.
5. **Settings > Pages** : sous « Branch », choisissez **main** et **/ (root)**, puis **Save**.
6. Après 2 à 5 minutes, l'annuaire est en ligne : `https://fasesif-png.github.io/annuaire-fasesif/`

## Étape 4 : tester puis inviter (10 minutes)

1. Ouvrez l'adresse de l'annuaire et entrez le **code coordinateur**.
2. Test : bouton **Codes**, copiez le code d'**Amiens**. Ouvrez une autre fenêtre privée avec l'annuaire, entrez ce code, puis **Remplir ma fiche > Envoyer pour validation**.
3. Vérifiez que la boîte mail de la FASESIF reçoit l'e-mail « fiche d'Amiens à valider ».
4. Côté coordinateur, actualisez la page, ouvrez **À valider** et cliquez sur **Refuser** (c'était un test).
5. Bouton **Codes** : envoyez à chaque président son invitation par **WhatsApp** ou **Copier** (lien et code déjà rédigés).

---

## Au quotidien

- **Être prévenu** : un e-mail arrive sur la boîte de la FASESIF à chaque fiche envoyée. L'adresse se règle avec la ligne `EMAIL_ALERTE` dans Apps Script ; `NOTIFIER_PAR_EMAIL = false` coupe les alertes. Après toute modification du script, redéployez une nouvelle version.
- **Valider** : bouton orange **À valider**. Une proposition validée est publiée aussitôt.
- **Tout voir à jour** : le tableur Google (onglet **Annuaire**) est la référence. L'onglet **Propositions** garde tout ce qui a été envoyé, l'onglet **Journal** garde qui a fait quoi. Le bouton **Excel** de l'annuaire télécharge un export.
- **Corriger à la main** : vous pouvez modifier les fiches directement dans le tableur ; l'annuaire se met à jour toutes les minutes.
- **Code perdu** : bouton **Codes** > icône ↻. L'ancien code est désactivé aussitôt.
- **Passation au bureau suivant** : transmettez les identifiants du compte Google et du compte GitHub de la FASESIF, ainsi que le code coordinateur. Vous pouvez aussi créer un nouveau code coordinateur dans l'onglet **Accès** (rôle « Coordinateur ») et désactiver l'ancien (Actif : Non).

## Règles importantes

- Ne renommez pas les **onglets** ni les **titres de colonnes** du tableur.
- Le dépôt GitHub est public mais ne contient **aucune donnée personnelle** : seulement l'application et l'adresse du service. Les fiches restent dans le tableur et ne sont envoyées qu'aux personnes qui ont un code valide.
- Les autres présidents ne voient le téléphone, l'e-mail et la photo d'une association que si son accord de diffusion est « Oui ».

## En cas de problème

| Message | Solution |
|---|---|
| Page GitHub « 404 » | Attendez 5 minutes. Vérifiez le nom du dépôt `annuaire-fasesif` et le réglage Pages **main / (root)**. |
| « Service non configuré » | L'URL n'est pas dans `config.js` (étape 3.4). |
| « Connexion impossible » | Déploiement en **Tout le monde** et URL qui se termine par `/exec`. |
| « Code non reconnu » | Recopiez le code depuis l'onglet **Accès**, sans espace. |
| « Le tableur n'est pas encore installé » | Relancez **installer** dans Apps Script. |
| Pas d'e-mail d'alerte | Vérifiez les spams, la ligne `EMAIL_ALERTE`, puis redéployez une nouvelle version. |
