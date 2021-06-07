---
title: Journal des modifications (Visual Studio Tools pour Unity, Mac) | Microsoft Docs
description: Affichez le journal des modifications pour Outils Visual Studio pour Unity, Mac. Consultez les modifications de version 1.0.0.0 à 2.7.0.0 et au-delà.
ms.custom: ''
ms.date: 6/3/2021
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: conceptual
ms.assetid: 33a6ac54-d997-4308-b5a0-af7387460849
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 2d3faf8e5231ca5d2e99bcf80dc18b6d4f4607cd
ms.sourcegitcommit: f430d014f912aa7874e1db65026dc72688b973e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111448296"
---
# <a name="change-log-visual-studio-tools-for-unity-mac"></a>Journal des modifications (Outils Visual Studio pour Unity, Mac)

Journal des modifications Visual Studio Tools pour Unity

## <a name="21020"></a>2.10.2.0
Publication : 2 juin 2021

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout d’un [`UNT0024`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0024.md) diagnostic. Donnez la priorité aux calculs scalaires sur les calculs de vecteurs.

- **Analyse**

  - Ajout de la prise en charge de l’utilisation de symboles PDB portables pour filtrer correctement les variables locales visibles.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction des annonces d’annonce de lecteur avec des versions Unity récentes.

## <a name="21010"></a>2.10.1.0
Publiée le 11 mai 2021

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résolution des problèmes de stabilité avec [`UNT0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0008.md) Quickfix.

  - Résolution des problèmes de performances avec les threads.

  - Correction des erreurs et des avertissements supprimés du filtrage dans le erreurs.

  - Résolution des processus d’arrière-plan Unity de filtrage.

## <a name="21000"></a>2.10.0.0
Publication : 13 avril 2021

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout d’un [`UNT0019`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0019.md) diagnostic. Appel d’indirection inutile pour `GameObject.gameObject` .

  - Ajout d’un [`UNT0020`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0020.md) diagnostic. `MenuItem` attribut utilisé sur une méthode non statique.

  - Ajout d’un [`UNT0021`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0021.md) diagnostic. Le message Unity doit être protégé (abonnement).

  - Ajout d’un [`UNT0022`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0022.md) diagnostic. Méthode inefficace pour définir la position et la rotation.

  - Ajout d’un [`UNT0023`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0023.md) diagnostic. Fusion de l’affectation sur les objets Unity.

  - Ajout [`USP0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0017.md) d’un suppresseur pour `IDE0074` . Les objets Unity ne doivent pas utiliser l’affectation de fusion.

## <a name="2940"></a>2.9.4.0
Publiée le 6 avril 2021

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résoudre les problèmes liés à l’énumération de test

## <a name="2930"></a>2.9.3.0
Publiée le 30 mars 2021

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résoudre les problèmes liés à Test Runner 

## <a name="2920"></a>2.9.2.0
Publication : 2 mars 2021

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de la mise en surbrillance dans la boîte de dialogue de message Unity.

  - Résolution des problèmes de stabilité avec le TreeView de projet Unity.

- **Débogage**

  - Correction du traitement des points d’arrêt conditionnels.

## <a name="2910"></a>2.9.1.0
Publiée le 9 février 2021

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge de l’exécution et du débogage des tests Unity à partir de l’IDE

- **Analyse**

  - Ajouté `Active Scene` aux variables locales, en présentant les objets de jeu racine.

  - Ajouté `this.gameObject` aux variables locales, étant donné qu’il est largement utilisé dans les projets Unity.

  - Ajout `Children` de `Components` groupes et à toutes les `GameObject` instances, ce qui vous permet d’afficher facilement l’ensemble de la hiérarchie d’objets.

  - Ajouté `Scene Path` à toutes les `GameObject` instances, pour afficher l’emplacement dans la scène.

  - Ajout de la prise en charge de `JobEntityBatch` /lambdas lors de l’utilisation d’entités avec des générateurs de code source.

  - Amélioration de la prise en charge de l’affichage de tableaux volumineux (à l’aide de compartiments d’index).

  - Ajout de messages Unity manquants pour l’API 2019,4.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résolution des problèmes de stabilité avec la boîte de dialogue de message Unity

  - Correction de divers problèmes de l’interface utilisateur pour les langues autres que fra.

  - Résolution des problèmes de stabilité avec le [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostic.

- **Débogage**

  - Résolution des problèmes de déconnexion de machine virtuelle lors de l’utilisation de `Trace` méthodes.

- **Analyse**

  - Correction du filtrage des propriétés obsolètes levant des exceptions.

## <a name="2900"></a>2.9.0.0
Publiée le 20 janvier 2021

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge des `raytrace shaders` `UXML` `USS` fichiers et.

  - API des messages Unity mise à jour (pour toutes les méthodes utilisées comme coroutines).

  - Détection de Android SDK mise à jour.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) du diagnostic, en donnant des avertissements incorrects pour les coroutines et `AssetPostprocessor.OnAssignMaterialModel` .

## <a name="2840"></a>2.8.4.0
Publiée le 15 décembre 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résolution d’un problème de fiabilité lors de la fermeture de l’Assistant Création d’événement Unity.

## <a name="2830"></a>2.8.3.0
Publication : 10 novembre 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Correction de l’attachement à Unity, même s’il n’y a aucun projet VSTU dans la solution.

## <a name="2820"></a>2.8.2.0
Publication : 27 octobre 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - [`UNT0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0010.md)Diagnostic amélioré pour s’appliquer à tous les éléments qui héritent de `Component` , et pas seulement `MonoBehaviour` .

## <a name="2810"></a>2.8.1.0
Publication : 13 octobre 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Analyse**

  - Ajout de la prise en charge de la conversion implicite avec les appels. Précédemment, l’évaluateur appliquait une vérification stricte des types, provoquant des `Failed to find a match for method([parameters...])` messages d’avertissement.

- **Intégration**

  - Ajout d’un [`UNT0018`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0018.md) diagnostic. Vous ne devez pas utiliser `System.Reflection` les fonctionnalités des messages critiques de performances comme `Update` , `FixedUpdate` , `LateUpdate` ou `OnGUI` .

  - Améliorations [`USP0003`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0003.md) et [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) suppressions, avec prise en charge de toutes les `AssetPostprocessor` méthodes statiques.

  - Ajout [`USP0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0016.md) d’un suppresseur pour `CS8618` . `C# 8.0` introduit les types référence Nullable et les types référence non Nullable. La détection de l’initialisation des types hérités de `UnityEngine.Object` n’est pas prise en charge et génère des erreurs.

  - À présent, à l’aide du même mécanisme de génération de projet Player et asmdef pour Unity 2019. x et 2020. x +.
  
  - Amélioration de l’expérience utilisateur lors de la génération de messages Unity avec un Assistant.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de la saisie semi-automatique inattendue des messages dans les commentaires.

## <a name="2800"></a>2.8.0.0 
Publiée le 14 septembre 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de la génération de projet de lecteur avec Unity 2019. x.

## <a name="2710"></a>2.7.1.0
Publiée le 5 août 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Mise à jour de l’API des messages Unity vers 2019,4.

  - Ajout [`USP0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0013.md) d’un suppresseur pour `CA1823` . Les champs privés avec `SerializeField` les `SerializeReference` attributs ou ne doivent pas être marqués comme étant inutilisés (FxCop).
  
  - Ajout [`USP0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0014.md) d’un suppresseur pour `CA1822` . Les messages Unity ne doivent pas être marqués comme candidats pour `static` Modifier (FxCop).

  - Ajout [`USP0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0015.md) d’un suppresseur pour `CA1801` . Les paramètres inutilisés ne doivent pas être supprimés des messages Unity (FxCop).
  
  - Ajout `MenuItem` de la prise en charge du [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) suppresseur.  

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Fixes [`USP0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0001.md) et des [`USP0002`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0002.md) suppressions qui ne fonctionnent pas avec des parenthèses supplémentaires ou des arguments de méthode.
  
  - Correction de l’actualisation de la base de données de ressources obligatoire même lorsque l’actualisation automatique a été désactivée dans les paramètres Unity.

## <a name="2700"></a>2.7.0.0
Publiée le 23 juin 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge de la persistance des dossiers solution lorsque Unity régénère la solution et les projets.

  - Ajout d’un [`UNT0015`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0015.md) diagnostic. Détectez une signature de méthode incorrecte avec l' `InitializeOnLoadMethod` `RuntimeInitializeOnLoadMethod` attribut ou.

  - Ajout d’un [`UNT0016`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0016.md) diagnostic. L’utilisation de `Invoke` , `InvokeRepeating` `StartCoroutine` ou `StopCoroutine` avec un premier argument qui est un littéral de chaîne n’est pas de type sécurisé.

  - Ajout d’un [`UNT0017`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0017.md) diagnostic. `SetPixels` l’appel est lent.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Correction de la création de points d’arrêt pendant l’exécution du jeu sur l’ancien Runtime mono (tentative de liaison du point d’arrêt dès qu’il est créé). 
  
- **Intégration**

  - Ne pas réinitialiser la sélection lors du filtrage des messages dans l’Assistant de message Unity.
  
  - Fixed [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md) , [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) et [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) les suppresseurs avec les règles suivantes : supprimer `IDE0044` (ReadOnly), `IDE0051` (inutilisé), `CS0649` (jamais affecté) pour tous les champs décorés avec l’attribut SerializeField. Supprimez `CS0649` (jamais affecté) pour les champs publics de tous les types qui développent `Unity.Object`.

  - Correction de la vérification des paramètres de type générique pour [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) .

- **Analyse**

  - Correction de la comparaison d’égalité avec les enums.

## <a name="2610"></a>2.6.1.0
Publiée le 19 mai 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Avertir si nous ne pouvons pas créer le serveur de messagerie côté Unity.

  - Exécuter correctement des analyseurs pendant la compilation légère.

  - Résolution de la documentation des API avec les installations d’Unit Hub.
  
  - Résolution des incidents du visualiseur du débogueur.

## <a name="2600"></a>2.6.0.0
Publiée le 14 avril 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout d’un [`UNT0012`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0012.md) diagnostic. Détectez et encapsulez les appels aux contre-routines dans `StartCoroutine()` .

  - Ajout d’un [`UNT0013`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0013.md) diagnostic. Détectez et supprimez l’attribut non valide ou redondant `SerializeField` .

  - Ajout d’un [`UNT0014`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0014.md) diagnostic. Détection `GetComponent()` appelée avec un type non-composant ou non-interface.

  - Ajout [`USP0009`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0009.md) d’un suppresseur pour `IDE0051` . Ne signalez pas les méthodes avec l' `ContextMenu` attribut ou référencées par un champ dont l’attribut n’est pas `ContextMenuItem` utilisé.

  - Ajout [`USP0010`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0010.md) d’un suppresseur pour `IDE0051` . Ne pas signaler les champs dont l’attribut n’est pas `ContextMenuItem` utilisé.

  - Ajout [`USP0011`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0011.md) d’un suppresseur pour `IDE0044` . Ne définissez pas de champs avec l' `ContextMenuItem` attribut en lecture seule.

  - [`USP0004`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0004.md), [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) et [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) fonctionnent à présent pour les `SerializeReference` `SerializeField` attributs et.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Envoie uniquement des commandes Démarrer/arrêter à Unity lorsque l’éditeur est en mesure de communiquer.

  - Correction de la documentation Express avec les messages hérités.

  - Correction de l’étendue du message pour le `CreateInspectorGUI` message.

  - N’effectuez pas [`UNT0001`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0001.md) de rapports sur les méthodes avec des modificateurs polymorphes.

- **Analyse**

  - Correction du traitement des alias using.
  
  - Correction du traitement des valeurs NULL.  

## <a name="2520"></a>2.5.2.0

Publication : 23 mars 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Correction de l’inscription des threads lors de l’attachement.

## <a name="2510"></a>2.5.1.0

Publication : 3 mars 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout [`USP0008`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0008.md) d’un suppresseur pour `IDE0051` . Les méthodes privées utilisées avec Invoke, InvokeRepeating, StartCoroutine ou StopCoroutine ne doivent pas être marquées comme étant inutilisées.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de la documentation OnDrawGizmos/OnDrawGizmosSelected.

- **Analyse**

  - Vérification de l’argument lambda fixe.

## <a name="2501"></a>2.5.0.1

Publiée le 19 février 2020

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction [`UNT0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/UNT0006.md) du diagnostic pour la signature de message incorrecte. Lors de l’inspection de types avec plusieurs niveaux d’héritage, ce diagnostic peut échouer avec le message suivant : `warning AD0001: Analyzer 'Microsoft.Unity.Analyzers.MessageSignatureAnalyzer' threw an exception of type 'System.ArgumentException' with message 'An item with the same key has already been added` .

## <a name="2500"></a>2.5.0.0

Publiée le 22 janvier 2020

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge des fichiers HLSL.
  
  - Basculer vers une interface utilisateur de boîte de dialogue Nouveau dossier.
  
  - Basculez vers une nouvelle grille de propriétés accessible pour les paramètres.

  - Ajout [`USP0006`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0006.md) d’un suppresseur pour `IDE0051` . Les champs privés avec l' `SerializeField` attribut ne doivent pas être marqués comme étant inutilisés.

  - Ajout [`USP0007`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0007.md) d’un suppresseur pour `CS0649` . Les champs avec l' `SerializeField` attribut ne doivent pas être marqués comme non assignés.  

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de la génération de projet (la `GenerateTargetFrameworkMonikerAttribute` cible n’était pas toujours localisée correctement).

- **Analyse**

  - Correction de l’évaluation de chaîne (sans utiliser les appels ToString ())

## <a name="2420"></a>2.4.2.0

Publication : 3 décembre 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction des diagnostics avec des interfaces définies par l’utilisateur.

  - Correction des info-bulles rapides avec des expressions mal formées.
  
## <a name="2410"></a>2.4.1.0 -327

Publication : 6 novembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge des processus d’arrière-plan Unity. (Le débogueur est en mesure de se connecter automatiquement au processus principal au lieu d’un processus enfant).

  - Ajout d’une info-bulle rapide pour les messages Unity, affichant la documentation associée.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de l’analyseur de comparaison de balises `UNT0002` avec des expressions binaires et d’appel avancées.

### <a name="deprecated-features"></a>Fonctionnalités déconseillées

- **Intégration**

  - À partir de là, Outils Visual Studio pour Unity ne prendra en charge que Visual Studio 2017 +.

## <a name="2400"></a>2.4.0.0

Publication : 15 octobre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout [`USP0005`](https://github.com/microsoft/Microsoft.Unity.Analyzers/blob/main/doc/USP0005.md) de suppresseur pour `IDE0060` (paramètre inutilisé) pour tous les messages Unity.

  - Ajout d’une info-bulle rapide pour les champs marqués avec `TooltipAttribute` . (Cela fonctionne également pour un accesseur Get simple à l’aide de ce champ).

## <a name="2330"></a>2.3.3.0

Publiée le 23 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout d’un nouveau suppresseur pour IDE0060, pour empêcher l’IDE d’illustrer un correctif rapide pour supprimer les paramètres inutilisés.
    - `USP0005` pour `IDE0060` : les messages Unity sont appelés par le runtime Unity.

## <a name="2320"></a>2.3.2.0

Publiée le 16 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Nous avons approfondi la compréhension de Visual Studio pour les projets Unity en ajoutant de nouveaux diagnostics spécifiques à Unity. Nous avons également rendu l’IDE plus intelligent en supprimant les diagnostics C# généraux qui ne s’appliquent pas aux projets Unity. Par exemple, l’IDE n’affiche pas de correctif rapide pour modifier une variable d’inspecteur `readonly` , ce qui vous empêche de modifier la variable dans l’éditeur Unity.
    - `UNT0001`: Les messages Unity sont appelés par le runtime même s’ils sont vides, ne les déclarent pas pour éviter le traitement uncesseray par le runtime Unity.
    - `UNT0002`: La comparaison des balises à l’aide de l’égalité des chaînes est plus lente que la méthode CompareTag intégrée.
    - `UNT0003`: L’utilisation de la forme générique de GetComponent est recommandée pour la sécurité de type.
    - `UNT0004`: Le message de mise à jour est dépendant de la fréquence des trames et doit utiliser Time. deltaTime au lieu de Time. fixedDeltaTime.
    - `UNT0005`: Le message FixedUpdate est indépendant de la fréquence d’images et doit utiliser Time. fixedDeltaTime au lieu de Time. deltaTime.
    - `UNT0006`: Une signature de méthode incorrecte a été détectée pour ce message Unity.
    - `UNT0007`: Unity remplace l’opérateur de comparaison null pour les objets Unity qui est incompatible avec la fusion de valeurs NULL.
    - `UNT0008`: Unity remplace l’opérateur de comparaison null pour les objets Unity qui est incompatible avec la propagation de null.
    - `UNT0009`: Lors de l’application de l’attribut InitializeOnLoad à une classe, vous devez fournir un constructeur statique. L’attribut InitializeOnLoad garantit qu’il sera appelé au lancement de l’éditeur.
    - `UNT0010`: Les monocomportements doivent être créés uniquement à l’aide de AddComponent (). Un MonoBehaviour est un composant et doit être attaché à un GameObject.
    - `UNT0011`: ScriptableObject doit être créé uniquement à l’aide de CreateInstance (). ScriptableObject doit être créé par le moteur Unity pour gérer les méthodes de message Unity.
    - `USP0001` pour `IDE0029` : les objets Unity ne doivent pas utiliser la fusion Null.
    - `USP0002` pour `IDE0031` : les objets Unity ne doivent pas utiliser la propagation null.
    - `USP0003` pour `IDE0051` : les messages Unity sont appelés par le runtime Unity.
    - `USP0004` pour `IDE0044` : les champs avec un attribut SerializeField ne doivent pas être rendus ReadOnly.

## <a name="2310"></a>2.3.1.0

Publication : 4 septembre 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Analyse**

  - Ajout de la prise en charge d’un meilleur affichage de type, c’est-à-dire `List<object>` au lieu de `List'1[[System.Object, <corlib...>]]` .

  - Ajout de la prise en charge de l’accès au membre pointeur, c.-à-d. `p->data->member` .

  - Ajout de la prise en charge des conversions implicites dans les initialiseurs de tableau, c.-à-d. `new byte [] {1,2,3,4}` .

  - Ajout de la prise en charge de l’éditeur hexadécimal lors de l’inspection des chaînes et des tableaux d’octets.

## <a name="2300"></a>2.3.0.0

Publication : 13 août 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Analyse**

  - Correction des problèmes d’exécution avec des exceptions.

  - Correction de l’évaluation des Pseudo-identificateurs (par exemple $exception).

  - Empêcher le blocage lors du déréférencement des adresses non valides.  

  - Correction du problème avec les AppDomains déchargés.

## <a name="2200"></a>2.2.0.0

Date de publication : 25 juillet 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Analyse**

  - Correction de l’inspection avec les types IntPtr.

- **Débogueur**

  - Correction de la gestion des catchpoints et des points d’arrêt de fonction.

## <a name="2130"></a>2.1.3.0

Date de publication : 9 juillet 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur**

  - Ajout de la prise en charge de l’interception des sous-classes d’exceptions.

  - Ajout de la prise en charge du protocole MDS 2.51.

- **Intégration**

  - Ajout de la prise en charge des fichiers asmdef.

  - Passage en mode Renommage quand un fichier est ajouté à partir d’un modèle (pour imiter le comportement de l’éditeur Unity).

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de la gestion des messages mal formés lors de la communication avec des joueurs Unity.

- **Analyse**

  - Correction de la gestion des espaces de noms dans les expressions.

## <a name="2120"></a>2.1.2.0

Date de publication : 2 juillet 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Analyse**

  - Correction du signalement d’erreurs avec des expressions non analysables.

## <a name="2110"></a>2.1.1.0

Publication : 27 juin 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Mise à jour de l’API MonoBehaviour vers 2019.1.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résolution des problèmes de performances de l’Explorateur de projets Unity.

  - Résolution des avertissements et erreurs de rapports à sortir lorsque le build léger est activé.

  - Résolution des performances du build léger.

## <a name="2100"></a>2.1.0.0

Publication : 20 juin 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Build complète désactivée pour les projets Unity, en faveur de l’utilisation des erreurs et des avertissements IntelliSense. En effet Unity crée une solution Visual Studio avec des projets de bibliothèque de classes qui représentent ce qu’Unity fait en interne. Cela étant dit, le résultat de la build dans Visual Studio n’est jamais utilisé ni prélevé par Unity lorsque leur pipeline de compilation est fermée. La génération dans Visual Studio consomme des ressources pour rien. Si vous avez besoin d’une build complète parce que vous avec des outils ou une installation qui en dépendent, vous pouvez désactiver cette optimisation (Paramètres/Outils pour Unity/Désactiver la build complète de projets).
  
  - Support ajouté pour les packages Unity dans l’UPE. Seuls les packages référencés (à l’aide de manifest.json dans le dossier `Packages`) et les packages locaux (incorporés dans le dossier `Packages`) sont visibles.

## <a name="2021"></a>2.0.2.1

Publication : 30 mai 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout d’une icône personnalisée pour les cibles d’exécution Unity.

## <a name="2020"></a>2.0.2.0

Publication : 2 avril 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Prise en charge de l’actualisation automatique de la base de données de la ressource Unity à l’enregistrement. Activée par défaut, cette fonctionnalité déclenche une recompilation côté Unity lors de l’enregistrement d’un script dans Visual Studio. Vous pouvez la désactiver dans Tools\Options\Tools for Unity\Refresh Unity’s AssetDatabase on save.

  - Prise en charge de la définition d’une installation par défaut de Unity pour la documentation hors connexion.

  - Ajout d’un menu contextuel au nouvel éditeur.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Résolution du filtrage d’assembly et de l’inspection des trames pour les trames vides.

## <a name="2011"></a>2.0.1.1
 
 Publication : 26 mars 2019

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Définition temporaire de Mono comme débogueur par défaut et seul débogueur utilisable pour cette version en particulier.

## <a name="2006"></a>2.0.0.6

Publication : 26 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Prise en charge de « Attacher à Unity et lire ».

## <a name="2005"></a>2.0.0.5

Publication : 20 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Conservation des propriétés externes lors du traitement du fichier solution.
  
- **Analyse**

  - Support ajouté pour les noms qualifiés d’alias (uniquement l’espace de noms global pour l’instant). Par conséquent, l’évaluateur d’expression accepte désormais les types utilisant le formulaire global::namespace.type.

  - Support ajouté pour le formulaire `pointer[index]`, sémantiquement identique au formulaire `*(pointer+index)` de déréférencement du pointeur.

## <a name="2004"></a>2.0.0.4

Publication : 5 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Mise à jour de l' `ScriptableObject` API.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Suppression des espaces de noms des modèles.

## <a name="2003"></a>2.0.0.3
 
 Publication : 5 mars 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Suppression des avertissements générés par les champs publics et sérialisés. Nous avons supprimé automatiquement les avertissements du `CS0649` `IDE0051` compilateur et dans les projets Unity qui ont créé ces messages.

- **Intégration**

  - Invite permettant de choisir une instance spécifique pour l’attachement en cas d’exécution de plusieurs processus Unity.

- **Analyse**

  - Prise en charge des fonctions locales.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Correction de la lecture des attributs personnalisés sur les arguments nommés avec d’anciennes versions des protocoles.

## <a name="2002"></a>2.0.0.2

Date de publication : 4 février 2019

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Mise à jour de l’API MonoBehaviour.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Résolution de la définition des valeurs primitives dans le débogueur.

## <a name="2001"></a>2.0.0.1

Publication : 4 décembre 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de l’autonomie du package d’installation.

## <a name="2000"></a>2.0.0.0
 Publication : 4 décembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur**

  - Remplacement du débogueur Unity sur Mac par le même débogueur Unity principal que Windows.

  - Remplacement de NRefactory par Roslyn pour l’évaluation des expressions.

  - Prise en charge des pointeurs : déréférencement, cast et arithmétique (Unity 2018.2 ou version ultérieure et nouveau runtime requis).

  - Prise en charge de l’affichage des pointeurs sous forme de tableau (comme en C++). Prenez une expression de pointeur, puis ajoutez-y une virgule et le nombre d’éléments à afficher.

  - Prise en charge des constructions asynchrones.

  - Prise en charge des pseudo-variables (identificateurs d’exception et d’objet).

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Correction de l’évaluation des expressions mal formées ou non prises en charge.

## <a name="1700"></a>1.7.0.0

Publication : 13 novembre 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur**

  - Ajout d’informations client supplémentaires (adresse IP, nom de la machine) dans la boîte de dialogue d’attachement.

### <a name="bug-fixes"></a>Résolution des bogues

- **Débogueur**

  - Correction d’un blocage dans la bibliothèque utilisée pour communiquer avec le moteur de débogage de Unity, à cause duquel Visual Studio ou Unity se figeait, en particulier lorsque l’on sélectionnait « Attacher à Unity » ou que l’on redémarrait le jeu.

- **Intégration**

  - Correction du problème d’activation du plug-in Unity lorsqu’un autre éditeur par défaut était sélectionné.

  - Correction du problème de création du modèle de fichier Unity.

## <a name="1602"></a>1.6.0.2

Publiée le 24 juillet 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Restauration de la solution de contournement d’un bogue de performances Unity corrigé par Unity.

## <a name="1601"></a>1.6.0.1

Publiée le 10 juillet 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Résolution du problème de pris en charge de la coloration de code du nuanceur.

## <a name="1600"></a>1.6.0.0

Publiée le 26 juin 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Assistants**

  - Faute de frappe corrigée pour le message de OnApplicationFocus.

- **Génération de projet :**

  - Solution de contournement temporaire pour un bogue de performances Unity : mise en cache de MonoIslands lors de la génération des projets.

  - Ne convertissez plus un fichier pdb portable en mdb lors de l’utilisation du nouveau runtime Unity.

## <a name="1502"></a>1.5.0.2

Publiée le 18 avril 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge de la complétion de code du nuanceur de base.

  - Ajout de la prise en charge de l’activation/désactivation des commentaires dans les fichiers du nuanceur.

## <a name="1501"></a>1.5.0.1

Publiée le 28 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge de modèles supplémentaires dans l’Explorateur de projets Unity.

## <a name="1500"></a>1.5.0.0

Publiée le 21 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge de la détection et de l’attachement pour les lecteurs Android connectés via USB.

## <a name="1403"></a>1.4.0.3

Publiée le 5 mars 2018

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge du nouveau générateur de projet dans Unity 2018.1.

- **Intégration**

  - Ajout d’un panneau d’options pour les paramètres dédiés.

## <a name="1402"></a>1.4.0.2

Publiée le 24 janvier 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Génération de projet :**

  - Détection de la version mono fixe.

- **Intégration**

  - Résolution des problèmes de synchronisation avec 2018.1 et activation du plug-in.

  - Correction des notifications lors de la détection d’un nouveau lecteur.

## <a name="1401"></a>1.4.0.1

Publiée le 23 janvier 2018

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction du développement/réduction des dossiers lors d’un double-clic

## <a name="1400"></a>1.4.0.0

Publiée le 13 décembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Génération de projet :**

  - Ajout de la prise en charge de .NET Standard.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction du problème de conversion automatique des symboles de débogage pdb-mdb.

## <a name="1301"></a>1.3.0.1

Publiée le 12 décembre 2017

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction de l’appel indirect à EditorPrefs.GetBool affectant l’inspecteur lors de la tentative de modifier la taille du tableau.

- **Assistants**

  - Actualiser le contexte roslyn avant d’insérer la méthode.

## <a name="1300"></a>1.3.0.0

Publiée le 20 novembre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Assistants**

  - Ajout de l’Assistant « Implémentation de message Unity ».

  - Ajout de la prise en charge de la nouvelle API de complétion dans Visual Studio pour Mac 7.4.

## <a name="1200"></a>1.2.0.0

Publiée le 23 octobre 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Débogueur**

  - Ajout de la prise en charge des fichiers de symboles de débogage portables.

### <a name="bug-fixes"></a>Résolution des bogues

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

- **Débogueur**

  - Démarrez la boîte de dialogue Attacher au processus si ne savez pas à quel Unity attacher.

- **Génération de projet :**

  - Activation de l’option du compilateur Autoriser le code unsafe quand Unity 5.6 est utilisé.

## <a name="1101"></a>1.1.0.1

Publiée le 20 juillet 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge des ressources localisées.

## <a name="1100"></a>1.1.0.0

Publiée le 12 juillet 2017

### <a name="new-features"></a>Nouvelles fonctionnalités

- **Intégration**

  - Ajout de la prise en charge de l’attachement à des lecteurs et des éditeurs via la fenêtre Attacher au processus.

- **Génération de projet :**

  - Correction des références de nom d’assembly avec des fichiers mcs.rsp.

  - Ajout de la prise en charge des unités de compilation assembly.json.

  - Correction des définitions avec des niveaux d’API.

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction du message d’erreur du nuanceur lors de la compilation.

## <a name="1001"></a>1.0.0.1

Publiée le 4 mai 2017

### <a name="bug-fixes"></a>Résolution des bogues

- **Intégration**

  - Correction du suivi de document actif avec les projets hybrides et réguliers.

## <a name="1000"></a>1.0.0.0

Publiée le 3 mai 2017
