---
title: Journal des modifications (Visual Studio Tools pour Unity, Mac) | Microsoft Docs
ms.custom: ''
ms.date: 12/02/2019
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: fe317d446ddc9196df02dfafcf0397f8815574c3
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74771541"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Journal des modifications (Outils Visual Studio pour Unity, Mac)

Journal des modifications Visual Studio Tools pour Unity

## <a name="2420"></a>2.4.2.0

Publication : 3 décembre 2019

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction des diagnostics avec des interfaces définies par l’utilisateur.

  - Correction des info-bulles rapides avec des expressions mal formées.
  
## <a name="2410"></a>2.4.1.0 -327

Publication : 6 novembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout de la prise en charge des processus d’arrière-plan Unity. (Le débogueur est en mesure de se connecter automatiquement au processus principal au lieu d’un processus enfant).

  - Ajout d’une info-bulle rapide pour les messages Unity, affichant la documentation associée.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction de l’analyseur de comparaison de balises `UNT0002` avec des expressions binaires et d’appel avancées.

### <a name="deprecated-features"></a>Fonctionnalités déconseillées

- **Intégration :**

  - À partir de là, Outils Visual Studio pour Unity ne prendra en charge que Visual Studio 2017 +.

## <a name="2400"></a>2.4.0.0

Publication : 15 octobre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout d’un suppresseur pour `IDE0060` (paramètre inutilisé) pour tous les messages Unity.

  - Ajout d’une info-bulle rapide pour les champs marqués avec `TooltipAttribute`. (Cela fonctionne également pour un accesseur Get simple à l’aide de ce champ).

## <a name="2330"></a>2.3.3.0

Publiée le 23 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout d’un nouveau suppresseur pour IDE0060, pour empêcher l’IDE d’illustrer un correctif rapide pour supprimer les paramètres inutilisés.
    - `USP0005` pour `IDE0060`: les messages Unity sont appelés par le runtime Unity.

## <a name="2320"></a>2.3.2.0

Publiée le 16 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Nous avons approfondi la compréhension de Visual Studio pour les projets Unity en ajoutant de nouveaux diagnostics spécifiques à Unity. Nous avons également rendu l’IDE plus intelligent en supprimant les diagnostics C# généraux qui ne s’appliquent pas aux projets Unity. Par exemple, l’IDE n’affiche pas de correctif rapide pour remplacer une variable d’inspecteur par `readonly` ce qui vous empêche de modifier la variable dans l’éditeur Unity.
    - `UNT0001`: les messages Unity sont appelés par le runtime même s’ils sont vides, ne les déclarent pas pour éviter le traitement uncesseray par le runtime Unity.
    - `UNT0002`: la comparaison des balises à l’aide de l’égalité des chaînes est plus lente que la méthode CompareTag intégrée.
    - `UNT0003`: l’utilisation de la forme générique de GetComponent est préférable à la sécurité de type.
    - `UNT0004`: le message de mise à jour est dépendant de la fréquence des images et doit utiliser Time. deltaTime au lieu de Time. fixedDeltaTime.
    - `UNT0005`: le message FixedUpdate est indépendant de la fréquence d’images et doit utiliser Time. fixedDeltaTime au lieu de Time. deltaTime.
    - `UNT0006`: une signature de méthode incorrecte a été détectée pour ce message Unity.
    - `UNT0007`: Unity remplace l’opérateur de comparaison null pour les objets Unity qui est incompatible avec la fusion de valeurs NULL.
    - `UNT0008`: Unity remplace l’opérateur de comparaison null pour les objets Unity qui est incompatible avec la propagation de null.
    - `UNT0009`: lors de l’application de l’attribut InitializeOnLoad à une classe, vous devez fournir un constructeur statique. L’attribut InitializeOnLoad garantit qu’il sera appelé au lancement de l’éditeur.
    - `UNT0010`: les monocomportements doivent être créés uniquement à l’aide de AddComponent (). Un MonoBehaviour est un composant et doit être attaché à un GameObject.
    - `UNT0011`: ScriptableObject doit être créé uniquement à l’aide de CreateInstance (). ScriptableObject doit être créé par le moteur Unity pour gérer les méthodes de message Unity.
    - `USP0001` pour `IDE0029`: les objets Unity ne doivent pas utiliser la fusion Null.
    - `USP0002` pour `IDE0031`: les objets Unity ne doivent pas utiliser la propagation null.
    - `USP0003` pour `IDE0051`: les messages Unity sont appelés par le runtime Unity.
    - `USP0004` pour `IDE0044`: les champs avec un attribut SerializeField ne doivent pas être rendus ReadOnly.

## <a name="2310"></a>2.3.1.0

Publication : 4 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Évaluation :**

  - Ajout de la prise en charge d’un meilleur affichage de type, c.-à-d. `List<object>` au lieu de `List'1[[System.Object, <corlib...>]]`.

  - Ajout de la prise en charge de l’accès aux membres du pointeur, c.-à-d. `p->data->member`.

  - Ajout de la prise en charge des conversions implicites dans les initialiseurs de tableau, c.-à-d. `new byte [] {1,2,3,4}`.

  - Ajout de la prise en charge de l’éditeur hexadécimal lors de l’inspection des chaînes et des tableaux d’octets.

## <a name="2300"></a>2.3.0.0

Publication : 13 août 2019

### <a name="bug-fixes"></a>Correctifs de bogues

- **Évaluation :**

  - Correction des problèmes d’exécution avec des exceptions.

  - Correction de l’évaluation des Pseudo-identificateurs (par exemple $exception).

  - Empêcher le blocage lors du déréférencement des adresses non valides.  

  - Correction du problème avec les AppDomains déchargés.

## <a name="2200"></a>2.2.0.0

Date de publication : 25 juillet 2019

### <a name="bug-fixes"></a>Correctifs de bogues

- **Évaluation :**

  - Correction de l’inspection avec les types IntPtr.

- **Débogueur :**

  - Correction de la gestion des catchpoints et des points d’arrêt de fonction.

## <a name="2130"></a>2.1.3.0

Date de publication : 9 juillet 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur :**

  - Ajout de la prise en charge de l’interception des sous-classes d’exceptions.

  - Ajout de la prise en charge du protocole MDS 2.51.

- **Intégration :**

  - Ajout de la prise en charge des fichiers asmdef.

  - Passage en mode Renommage quand un fichier est ajouté à partir d’un modèle (pour imiter le comportement de l’éditeur Unity).

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction de la gestion des messages mal formés lors de la communication avec des joueurs Unity.

- **Évaluation :**

  - Correction de la gestion des espaces de noms dans les expressions.

## <a name="2120"></a>2.1.2.0

Date de publication : 2 juillet 2019

### <a name="bug-fixes"></a>Correctifs de bogues

- **Évaluation :**

  - Correction du signalement d’erreurs avec des expressions non analysables.

## <a name="2110"></a>2.1.1.0

Publication : 27 juin 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Mise à jour de l’API MonoBehaviour vers 2019.1.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Résolution des problèmes de performances de l’Explorateur de projets Unity.

  - Résolution des avertissements et erreurs de rapports à sortir lorsque le build léger est activé.

  - Résolution des performances du build léger.

## <a name="2100"></a>2.1.0.0

Publication : 20 juin 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Build complète désactivée pour les projets Unity, en faveur de l’utilisation des erreurs et des avertissements IntelliSense. En effet Unity crée une solution Visual Studio avec des projets de bibliothèque de classes qui représentent ce qu’Unity fait en interne. Cela étant dit, le résultat de la build dans Visual Studio n’est jamais utilisé ni prélevé par Unity lorsque leur pipeline de compilation est fermée. La génération dans Visual Studio consomme des ressources pour rien. Si vous avez besoin d’une build complète parce que vous avec des outils ou une installation qui en dépendent, vous pouvez désactiver cette optimisation (Paramètres/Outils pour Unity/Désactiver la build complète de projets).
  
  - Support ajouté pour les packages Unity dans l’UPE. Seuls les packages référencés (à l’aide de manifest.json dans le dossier `Packages`) et les packages locaux (incorporés dans le dossier `Packages`) sont visibles.

## <a name="2021"></a>2.0.2.1

Publication : 30 mai 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout d’une icône personnalisée pour les cibles d’exécution Unity.

## <a name="2020"></a>2.0.2.0

Publication : 2 avril 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Prise en charge de l’actualisation automatique de la base de données de la ressource Unity à l’enregistrement. Activée par défaut, cette fonctionnalité déclenche une recompilation côté Unity lors de l’enregistrement d’un script dans Visual Studio. Vous pouvez la désactiver dans Tools\Options\Tools for Unity\Refresh Unity’s AssetDatabase on save.

  - Prise en charge de la définition d’une installation par défaut de Unity pour la documentation hors connexion.

  - Ajout d’un menu contextuel au nouvel éditeur.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Débogueur :**

  - Résolution du filtrage d’assembly et de l’inspection des trames pour les trames vides.

## <a name="2011"></a>2.0.1.1
 
 Publication : 26 mars 2019

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Définition temporaire de Mono comme débogueur par défaut et seul débogueur utilisable pour cette version en particulier.

## <a name="2006"></a>2.0.0.6

Publication : 26 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Prise en charge de « Attacher à Unity et lire ».

## <a name="2005"></a>2.0.0.5

Publication : 20 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Conservation des propriétés externes lors du traitement du fichier solution.
  
- **Évaluation :**

  - Support ajouté pour les noms qualifiés d’alias (uniquement l’espace de noms global pour l’instant). Par conséquent, l’évaluateur d’expression accepte désormais les types utilisant le formulaire global::namespace.type.

  - Support ajouté pour le formulaire `pointer[index]`, sémantiquement identique au formulaire `*(pointer+index)` de déréférencement du pointeur.

## <a name="2004"></a>2.0.0.4

Publication : 5 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Mise à jour de l’API `ScriptableObject`.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Suppression des espaces de noms des modèles.

## <a name="2003"></a>2.0.0.3
 
 Publication : 5 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Suppression des avertissements générés par les champs publics et sérialisés. Nous avons supprimé automatiquement les avertissements du compilateur `CS0649` et `IDE0051` dans les projets Unity qui ont créé ces messages.

- **Intégration :**

  - Invite permettant de choisir une instance spécifique pour l’attachement en cas d’exécution de plusieurs processus Unity.

- **Évaluation :**

  - Prise en charge des fonctions locales.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Débogueur :**

  - Correction de la lecture des attributs personnalisés sur les arguments nommés avec d’anciennes versions des protocoles.

## <a name="2002"></a>2.0.0.2

Publication : 4 février 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Mise à jour de l’API MonoBehaviour.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Débogueur :**

  - Résolution de la définition des valeurs primitives dans le débogueur.

## <a name="2001"></a>2.0.0.1

Publication : 4 décembre 2018

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction de l’autonomie du package d’installation.

## <a name="2000"></a>2.0.0.0
 Publication : 4 décembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur :**

  - Remplacement du débogueur Unity sur Mac par le même débogueur Unity principal que Windows.

  - Remplacement de NRefactory par Roslyn pour l’évaluation des expressions.

  - Prise en charge des pointeurs : déréférencement, cast et arithmétique (Unity 2018.2 ou version ultérieure et nouveau runtime requis).

  - Prise en charge de l’affichage des pointeurs sous forme de tableau (comme en C++). Prenez une expression de pointeur, puis ajoutez-y une virgule et le nombre d’éléments à afficher.

  - Prise en charge des constructions asynchrones.

  - Prise en charge des pseudo-variables (identificateurs d’exception et d’objet).

### <a name="bug-fixes"></a>Correctifs de bogues

- **Débogueur :**

  - Correction de l’évaluation des expressions mal formées ou non prises en charge.

## <a name="1700"></a>1.7.0.0

Publication : 13 novembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur :**

  - Ajout d’informations client supplémentaires (adresse IP, nom de la machine) dans la boîte de dialogue d’attachement.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Débogueur :**

  - Correction d’un blocage dans la bibliothèque utilisée pour communiquer avec le moteur de débogage de Unity, à cause duquel Visual Studio ou Unity se figeait, en particulier lorsque l’on sélectionnait « Attacher à Unity » ou que l’on redémarrait le jeu.

- **Intégration :**

  - Correction du problème d’activation du plug-in Unity lorsqu’un autre éditeur par défaut était sélectionné.

  - Correction du problème de création du modèle de fichier Unity.

## <a name="1602"></a>1.6.0.2

Publiée le 24 juillet 2018

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Restauration de la solution de contournement d’un bogue de performances Unity corrigé par Unity.

## <a name="1601"></a>1.6.0.1

Publiée le 10 juillet 2018

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Résolution du problème de pris en charge de la coloration de code du nuanceur.

## <a name="1600"></a>1.6.0.0

Publiée le 26 juin 2018

### <a name="bug-fixes"></a>Correctifs de bogues

- **Assistants :**

  - Faute de frappe corrigée pour le message de OnApplicationFocus.

- **Génération de projet :**

  - Solution de contournement temporaire pour un bogue de performances Unity : mise en cache de MonoIslands lors de la génération des projets.

  - Ne convertissez plus un fichier pdb portable en mdb lors de l’utilisation du nouveau runtime Unity.

## <a name="1502"></a>1.5.0.2

Publiée le 18 avril 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout de la prise en charge de la complétion de code du nuanceur de base.

  - Ajout de la prise en charge de l’activation/désactivation des commentaires dans les fichiers du nuanceur.

## <a name="1501"></a>1.5.0.1

Publiée le 28 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout de la prise en charge de modèles supplémentaires dans l’Explorateur de projets Unity.

## <a name="1500"></a>1.5.0.0

Publiée le 21 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout de la prise en charge de la détection et de l’attachement pour les lecteurs Android connectés via USB.

## <a name="1403"></a>1.4.0.3

Publiée le 5 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge du nouveau générateur de projet dans Unity 2018.1.

- **Intégration :**

  - Ajout d’un panneau d’options pour les paramètres dédiés.

## <a name="1402"></a>1.4.0.2

Publiée le 24 janvier 2018

### <a name="bug-fixes"></a>Correctifs de bogues

- **Génération de projet :**

  - Détection de la version mono fixe.

- **Intégration :**

  - Résolution des problèmes de synchronisation avec 2018.1 et activation du plug-in.

  - Correction des notifications lors de la détection d’un nouveau lecteur.

## <a name="1401"></a>1.4.0.1

Publiée le 23 janvier 2018

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction du développement/réduction des dossiers lors d’un double-clic

## <a name="1400"></a>1.4.0.0

Publiée le 13 décembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge de .NET Standard.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction du problème de conversion automatique des symboles de débogage pdb-mdb.

## <a name="1301"></a>1.3.0.1

Publiée le 12 décembre 2017

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction de l’appel indirect à EditorPrefs.GetBool affectant l’inspecteur lors de la tentative de modifier la taille du tableau.

- **Assistants :**

  - Actualiser le contexte roslyn avant d’insérer la méthode.

## <a name="1300"></a>1.3.0.0

Publiée le 20 novembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Assistants :**

  - Ajout de l’Assistant « Implémentation de message Unity ».

  - Ajout de la prise en charge de la nouvelle API de complétion dans Visual Studio pour Mac 7.4.

## <a name="1200"></a>1.2.0.0

Publiée le 23 octobre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur :**

  - Ajout de la prise en charge des fichiers de symboles de débogage portables.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Génération de projet :**

  - Correction du problème de l’ajout d’une extension .dll supplémentaire au nom du fichier d’assembly.

  - Ne forcez pas l’indicateur Unity AllowAttachedDebuggingOfEditor, car la valeur par défaut est maintenant true.

## <a name="1103"></a>1.1.0.3

Publiée le 23 octobre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge du profil .NET 4.6.

## <a name="1102"></a>1.1.0.2

Publiée le 8 août 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur :**

  - Démarrez la boîte de dialogue Attacher au processus si ne savez pas à quel Unity attacher.

- **Génération de projet :**

  - Activation de l’option du compilateur Autoriser le code unsafe quand Unity 5.6 est utilisé.

## <a name="1101"></a>1.1.0.1

Publiée le 20 juillet 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout de la prise en charge des ressources localisées.

## <a name="1100"></a>1.1.0.0

Publiée le 12 juillet 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration :**

  - Ajout de la prise en charge de l’attachement à des lecteurs et des éditeurs via la fenêtre Attacher au processus.

- **Génération de projet :**

  - Correction des références de nom d’assembly avec des fichiers mcs.rsp.

  - Ajout de la prise en charge des unités de compilation assembly.json.

  - Correction des définitions avec des niveaux d’API.

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction du message d’erreur du nuanceur lors de la compilation.

## <a name="1001"></a>1.0.0.1

Publiée le 4 mai 2017

### <a name="bug-fixes"></a>Correctifs de bogues

- **Intégration :**

  - Correction du suivi de document actif avec les projets hybrides et réguliers.

## <a name="1000"></a>1.0.0.0

Publiée le 3 mai 2017
