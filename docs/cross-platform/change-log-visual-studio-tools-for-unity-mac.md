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
ms.openlocfilehash: 5599153f79b273249e93c48aaa197214d92f5fe7
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232921"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Journal des modifications (Outils Visual Studio pour Unity, Mac)

Journal des modifications Visual Studio Tools pour Unity

## <a name="2520"></a>2.5.2.0

Sortie le 23 mars 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur:**

  - Enregistrement fixe des threads à l’attacher.

## <a name="2510"></a>2.5.1.0

Sortie le 3 mars 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajouté un suppresseur pour [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0008.md). Les méthodes privées utilisées avec Invoke, InvokeRepeating, StartCoroutine ou StopCoroutine ne doivent pas être marquées comme inutilisées.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Documentation sur la liste onDrawGizmos/OnDrawGizmosS

- **Évaluation:**

  - Inspection fixe de l’argument lambda.

## <a name="2501"></a>2.5.0.1

Sortie le 19 février 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Vérification [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/UNT0006.md) diagnostique fixe pour la signature incorrecte de message. Lors de l’inspection des types avec plusieurs niveaux d’héritage, ce diagnostic pourrait échouer avec le message suivant: `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added`.

## <a name="2500"></a>2.5.0.0

Sortie le 22 janvier 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout d’un support pour les fichiers HLSL.
  
  - Passé à une nouvelle interface utilisateur de dialogue de dossier.
  
  - Passage à une nouvelle grille de propriété accessible pour les paramètres.

  - Ajouté un suppresseur pour [`IDE0051`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0006.md). Les champs `SerializeField` privés avec l’attribut ne doivent pas être marqués comme inutilisés.

  - Ajouté un suppresseur pour [`CS0649`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/master/doc/USP0007.md). Les champs `SerializeField` avec l’attribut ne doivent pas être marqués comme non affectés.  

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Génération fixe`GenerateTargetFrameworkMonikerAttribute` de projet (la cible n’était pas toujours localisée correctement)

- **Évaluation:**

  - Évaluation des cordes fixes (non à l’aide d’appels ToString))

## <a name="2420"></a>2.4.2.0

Sortie le 3 décembre 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Diagnostics fixes avec interfaces définies par l’utilisateur.

  - Des outils rapides fixes avec des expressions mal formées.
  
## <a name="2410"></a>2.4.1.0

Sortie le 6 novembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout d’un soutien aux processus de fond Unity. (Le débbuggeur est capable de se connecter automatiquement au processus principal au lieu d’un processus pour enfants).

  - Ajout d’un outil rapide pour les messages Unity, affichant la documentation associée.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction de l’analyseur `UNT0002` de comparaison de tag avec des expressions binaires et d’invocation avancées.

### <a name="deprecated-features"></a>Fonctionnalités déconseillées

- **Intégration:**

  - À l’avenir, Visual Studio Tools for Unity ne prendra en charge Visual Studio 2017.

## <a name="2400"></a>2.4.0.0

Sortie le 15 octobre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout d’un `IDE0060` suppresseur pour (paramètre inutilisé) pour tous les messages Unity.

  - Ajouté un tooltip rapide pour `TooltipAttribute`les champs marqués avec . (Cela fonctionnera pour un accesseur simple obtenir en utilisant ce domaine ainsi).

## <a name="2330"></a>2.3.3.0

Sortie le 23 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout d’un nouveau suppresseur pour IDE0060, pour empêcher l’IDE d’afficher une solution rapide pour supprimer les paramètres inutilisés.
    - `USP0005`pour `IDE0060`: Les messages d’unité sont invoqués par le runtime Unity.

## <a name="2320"></a>2.3.2.0

Sortie le 16 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Nous avons approfondi la compréhension que Visual Studio a pour les projets Unity en ajoutant de nouveaux diagnostics spécifiques à l’unité. Nous avons également rendu l’IDE plus intelligent en supprimant les diagnostics C# généraux qui ne s’appliquent pas aux projets Unity. Par exemple, l’IDE ne montrera pas une solution `readonly` rapide pour modifier une variable d’inspecteur à laquelle vous empêcherait de modifier la variable dans l’éditeur d’unité.
    - `UNT0001`: Les messages d’unité sont appelés par le temps d’exécution même s’ils sont vides, ne les déclarent pas pour éviter le traitement uncesseray par le runtime d’unité.
    - `UNT0002`: La comparaison des étiquettes en utilisant l’égalité des cordes est plus lente que la méthode CompareTag intégrée.
    - `UNT0003`: L’utilisation de la forme générique de GetComponent est préférable pour la sécurité de type.
    - `UNT0004`: Le message de mise à jour dépend du taux d’image et devrait utiliser Time.deltaTime au lieu de Time.fixedDeltaTime.
    - `UNT0005`: Le message FixedUpdate est indépendant de taux d’image et doit utiliser Time.fixedDeltaTime au lieu de Time.deltaTime.
    - `UNT0006`: Une signature de méthode incorrecte a été détectée pour ce message Unity.
    - `UNT0007`: Unity remplace l’opérateur de comparaison nul pour les objets Unity qui est incompatible avec la fusion nulle.
    - `UNT0008`: Unity remplace l’opérateur de comparaison nul pour les objets Unity qui est incompatible avec la propagation nulle.
    - `UNT0009`: Lors de l’application de l’attribut InitializeOnLoad à une classe, vous devez fournir un constructeur statique. L’attribut InitializeOnLoad garantit qu’il sera appelé au lancement de l’éditeur.
    - `UNT0010`: Les monobehaviours ne doivent être créés qu’à l’aide d’AddComponent(). Un MonoBehaviour est un composant et doit être attaché à un GameObject.
    - `UNT0011`: ScriptableObject ne doit être créé qu’à l’aide de CreateInstance(). ScriptableObject doit être créé par le moteur Unity pour gérer les méthodes de message Unity.
    - `USP0001`pour `IDE0029`: Les objets d’unité ne doivent pas utiliser la fusion nulle.
    - `USP0002`pour `IDE0031`: Les objets Unity ne doivent pas utiliser la propagation nulle.
    - `USP0003`pour `IDE0051`: Les messages d’unité sont invoqués par le runtime Unity.
    - `USP0004`pour `IDE0044`: Les champs avec un attribut SerializeField ne doivent pas être faits readonly.

## <a name="2310"></a>2.3.1.0

Sortie le 4 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Évaluation:**

  - Ajout d’un support pour un `List<object>` meilleur `List'1[[System.Object, <corlib...>]]`écran de type, c’est-à-dire au lieu de .

  - Ajout d’un soutien pour l’accès des membres pointeurs, c’est-à-dire `p->data->member`.

  - Ajout d’un support pour les conversions implicites dans les initialisateurs de tableau, c’est-à-dire . `new byte [] {1,2,3,4}`

  - Ajout d’un support pour l’éditeur hex lors de l’inspection des tableaux et des cordes d’byte.

## <a name="2300"></a>2.3.0.0

Sortie le 13 août 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Évaluation:**

  - Problèmes de passament fixes avec des exceptions.

  - Évaluation fixe des pseudo-identificateurs (comme $exception).

  - Prévenir l’accident lors du report des adresses invalides.  

  - Problème fixe avec appdomains déchargés.

## <a name="2200"></a>2.2.0.0

Date de publication : 25 juillet 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Évaluation:**

  - Correction de l’inspection avec les types IntPtr.

- **Débogueur:**

  - Correction de la gestion des catchpoints et des points d’arrêt de fonction.

## <a name="2130"></a>2.1.3.0

Date de publication : 9 juillet 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur:**

  - Ajout de la prise en charge de l’interception des sous-classes d’exceptions.

  - Ajout de la prise en charge du protocole MDS 2.51.

- **Intégration:**

  - Ajout de la prise en charge des fichiers asmdef.

  - Passage en mode Renommage quand un fichier est ajouté à partir d’un modèle (pour imiter le comportement de l’éditeur Unity).

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction de la gestion des messages mal formés lors de la communication avec des joueurs Unity.

- **Évaluation:**

  - Correction de la gestion des espaces de noms dans les expressions.

## <a name="2120"></a>2.1.2.0

Date de publication : 2 juillet 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Évaluation:**

  - Correction du signalement d’erreurs avec des expressions non analysables.

## <a name="2110"></a>2.1.1.0

Publication : 27 juin 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Mise à jour de l’API MonoBehaviour vers 2019.1.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Résolution des problèmes de performances de l’Explorateur de projets Unity.

  - Résolution des avertissements et erreurs de rapports à sortir lorsque le build léger est activé.

  - Résolution des performances du build léger.

## <a name="2100"></a>2.1.0.0

Publication : 20 juin 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Build complète désactivée pour les projets Unity, en faveur de l’utilisation des erreurs et des avertissements IntelliSense. En effet Unity crée une solution Visual Studio avec des projets de bibliothèque de classes qui représentent ce qu’Unity fait en interne. Cela étant dit, le résultat de la build dans Visual Studio n’est jamais utilisé ni prélevé par Unity lorsque leur pipeline de compilation est fermée. La génération dans Visual Studio consomme des ressources pour rien. Si vous avez besoin d’une build complète parce que vous avec des outils ou une installation qui en dépendent, vous pouvez désactiver cette optimisation (Paramètres/Outils pour Unity/Désactiver la build complète de projets).
  
  - Support ajouté pour les packages Unity dans l’UPE. Seuls les packages référencés (à l’aide de manifest.json dans le dossier `Packages`) et les packages locaux (incorporés dans le dossier `Packages`) sont visibles.

## <a name="2021"></a>2.0.2.1

Publication : 30 mai 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout d’une icône personnalisée pour les cibles d’exécution Unity.

## <a name="2020"></a>2.0.2.0

Publication : 2 avril 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Prise en charge de l’actualisation automatique de la base de données de la ressource Unity à l’enregistrement. Activée par défaut, cette fonctionnalité déclenche une recompilation côté Unity lors de l’enregistrement d’un script dans Visual Studio. Vous pouvez la désactiver dans Tools\Options\Tools for Unity\Refresh Unity’s AssetDatabase on save.

  - Prise en charge de la définition d’une installation par défaut de Unity pour la documentation hors connexion.

  - Ajout d’un menu contextuel au nouvel éditeur.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur:**

  - Résolution du filtrage d’assembly et de l’inspection des trames pour les trames vides.

## <a name="2011"></a>2.0.1.1
 
 Publication : 26 mars 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Définition temporaire de Mono comme débogueur par défaut et seul débogueur utilisable pour cette version en particulier.

## <a name="2006"></a>2.0.0.6

Publication : 26 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Prise en charge de « Attacher à Unity et lire ».

## <a name="2005"></a>2.0.0.5

Publication : 20 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Conservation des propriétés externes lors du traitement du fichier solution.
  
- **Évaluation:**

  - Support ajouté pour les noms qualifiés d’alias (uniquement l’espace de noms global pour l’instant). Par conséquent, l’évaluateur d’expression accepte désormais les types utilisant le formulaire global::namespace.type.

  - Support ajouté pour le formulaire `pointer[index]`, sémantiquement identique au formulaire `*(pointer+index)` de déréférencement du pointeur.

## <a name="2004"></a>2.0.0.4

Publication : 5 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Mise `ScriptableObject` à jour de l’API.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Suppression des espaces de noms des modèles.

## <a name="2003"></a>2.0.0.3
 
 Publication : 5 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Suppression des avertissements générés par les champs publics et sérialisés. Nous avons supprimé automatiquement `CS0649` les `IDE0051` avertissements et les compilateur dans les projets Unity qui ont créé ces messages.

- **Intégration:**

  - Invite permettant de choisir une instance spécifique pour l’attachement en cas d’exécution de plusieurs processus Unity.

- **Évaluation:**

  - Prise en charge des fonctions locales.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur:**

  - Correction de la lecture des attributs personnalisés sur les arguments nommés avec d’anciennes versions des protocoles.

## <a name="2002"></a>2.0.0.2

Publication : 4 février 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Mise à jour de l’API MonoBehaviour.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur:**

  - Résolution de la définition des valeurs primitives dans le débogueur.

## <a name="2001"></a>2.0.0.1

Publication : 4 décembre 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction de l’autonomie du package d’installation.

## <a name="2000"></a>2.0.0.0
 Publication : 4 décembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur:**

  - Remplacement du débogueur Unity sur Mac par le même débogueur Unity principal que Windows.

  - Remplacement de NRefactory par Roslyn pour l’évaluation des expressions.

  - Prise en charge des pointeurs : déréférencement, cast et arithmétique (Unity 2018.2 ou version ultérieure et nouveau runtime requis).

  - Prise en charge de l’affichage des pointeurs sous forme de tableau (comme en C++). Prenez une expression de pointeur, puis ajoutez-y une virgule et le nombre d’éléments à afficher.

  - Prise en charge des constructions asynchrones.

  - Prise en charge des pseudo-variables (identificateurs d’exception et d’objet).

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur:**

  - Correction de l’évaluation des expressions mal formées ou non prises en charge.

## <a name="1700"></a>1.7.0.0

Publication : 13 novembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur:**

  - Ajout d’informations client supplémentaires (adresse IP, nom de la machine) dans la boîte de dialogue d’attachement.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur:**

  - Correction d’un blocage dans la bibliothèque utilisée pour communiquer avec le moteur de débogage de Unity, à cause duquel Visual Studio ou Unity se figeait, en particulier lorsque l’on sélectionnait « Attacher à Unity » ou que l’on redémarrait le jeu.

- **Intégration:**

  - Correction du problème d’activation du plug-in Unity lorsqu’un autre éditeur par défaut était sélectionné.

  - Correction du problème de création du modèle de fichier Unity.

## <a name="1602"></a>1.6.0.2

Publiée le 24 juillet 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Restauration de la solution de contournement d’un bogue de performances Unity corrigé par Unity.

## <a name="1601"></a>1.6.0.1

Publiée le 10 juillet 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Résolution du problème de pris en charge de la coloration de code du nuanceur.

## <a name="1600"></a>1.6.0.0

Publiée le 26 juin 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Assistants :**

  - Faute de frappe corrigée pour le message de OnApplicationFocus.

- **Génération de projet :**

  - Solution de contournement temporaire pour un bogue de performances Unity : mise en cache de MonoIslands lors de la génération des projets.

  - Ne convertissez plus un fichier pdb portable en mdb lors de l’utilisation du nouveau runtime Unity.

## <a name="1502"></a>1.5.0.2

Publiée le 18 avril 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout de la prise en charge de la complétion de code du nuanceur de base.

  - Ajout de la prise en charge de l’activation/désactivation des commentaires dans les fichiers du nuanceur.

## <a name="1501"></a>1.5.0.1

Publiée le 28 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout de la prise en charge de modèles supplémentaires dans l’Explorateur de projets Unity.

## <a name="1500"></a>1.5.0.0

Publiée le 21 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout de la prise en charge de la détection et de l’attachement pour les lecteurs Android connectés via USB.

## <a name="1403"></a>1.4.0.3

Publiée le 5 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge du nouveau générateur de projet dans Unity 2018.1.

- **Intégration:**

  - Ajout d’un panneau d’options pour les paramètres dédiés.

## <a name="1402"></a>1.4.0.2

Publiée le 24 janvier 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Génération de projet :**

  - Détection de la version mono fixe.

- **Intégration:**

  - Résolution des problèmes de synchronisation avec 2018.1 et activation du plug-in.

  - Correction des notifications lors de la détection d’un nouveau lecteur.

## <a name="1401"></a>1.4.0.1

Publiée le 23 janvier 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction du développement/réduction des dossiers lors d’un double-clic

## <a name="1400"></a>1.4.0.0

Publiée le 13 décembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge de .NET Standard.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction du problème de conversion automatique des symboles de débogage pdb-mdb.

## <a name="1301"></a>1.3.0.1

Publiée le 12 décembre 2017

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction de l’appel indirect à EditorPrefs.GetBool affectant l’inspecteur lors de la tentative de modifier la taille du tableau.

- **Assistants :**

  - Actualiser le contexte roslyn avant d’insérer la méthode.

## <a name="1300"></a>1.3.0.0

Publiée le 20 novembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Assistants :**

  - Ajout de l’Assistant « Implémentation de message Unity ».

  - Ajout de la prise en charge de la nouvelle API de complétion dans Visual Studio pour Mac 7.4.

## <a name="1200"></a>1.2.0.0

Publiée le 23 octobre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur:**

  - Ajout de la prise en charge des fichiers de symboles de débogage portables.

### <a name="bug-fixes"></a>Résolution des bogues

- **Génération de projet :**

  - Correction du problème de l’ajout d’une extension .dll supplémentaire au nom du fichier d’assembly.

  - Ne forcez pas l’indicateur Unity AllowAttachedDebuggingOfEditor, car la valeur par défaut est maintenant true.

## <a name="1103"></a>1.1.0.3

Publiée le 23 octobre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge du profil .NET 4.6.

## <a name="1102"></a>1.1.0.2

Publiée le 8 août 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur:**

  - Démarrez la boîte de dialogue Attacher au processus si ne savez pas à quel Unity attacher.

- **Génération de projet :**

  - Activation de l’option du compilateur Autoriser le code unsafe quand Unity 5.6 est utilisé.

## <a name="1101"></a>1.1.0.1

Publiée le 20 juillet 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout de la prise en charge des ressources localisées.

## <a name="1100"></a>1.1.0.0

Publiée le 12 juillet 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration:**

  - Ajout de la prise en charge de l’attachement à des lecteurs et des éditeurs via la fenêtre Attacher au processus.

- **Génération de projet :**

  - Correction des références de nom d’assembly avec des fichiers mcs.rsp.

  - Ajout de la prise en charge des unités de compilation assembly.json.

  - Correction des définitions avec des niveaux d’API.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction du message d’erreur du nuanceur lors de la compilation.

## <a name="1001"></a>1.0.0.1

Publiée le 4 mai 2017

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration:**

  - Correction du suivi de document actif avec les projets hybrides et réguliers.

## <a name="1000"></a>1.0.0.0

Publiée le 3 mai 2017
