---
title: Journal des modifications (Visual Studio Tools pour Unity) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea490b7e-fc0d-44b1-858a-a725ce20e396
caps.latest.revision: 14
author: conceptdev
ms.author: crdun
manager: ghogen
ms.openlocfilehash: e23608f3fbbb14bd6d8f8c0494cb1ae2784358fa
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837967"
---
# <a name="change-log-visual-studio-tools-for-unity"></a>Journal des modifications (Visual Studio Tools pour Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Journal des modifications Visual Studio Tools pour Unity

## <a name="23"></a>2.3
 Publication : 14-07-2016

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Général :**

    -   Ajout d’une option pour désactiver les journaux de console Unity dans la liste d’erreurs de Visual Studio.

    -   Ajout d’une option pour autoriser la modification des propriétés de projet générées.

-   **Débogueur :**

    -   Ajout des visualiseurs de chaînes de texte, XML, HTML et JSON.

-   **Assistants :**

    -   Ajout de MonoBehaviors manquants.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Général :**

    -   Résolution d’un conflit lié à ReSharper, qui empêchait l’affichage des contrôles dans les paramètres de Visual Studio.

    -   Résolution d’un conflit lié à Xamarin, qui empêchait le débogage dans certaines situations.

-   **Débogueur :**

    -   Correction d’un problème provoquant le blocage de Visual Studio pendant le débogage.

    -   Correction d’un problème lié aux points d’arrêt de fonction dans Visual Studio 2015.

    -   Correction de plusieurs problèmes d’évaluation d’expression.

## <a name="22"></a>2.2
 Publication 04-02-2016

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Assistants :**

    -   Ajout de la recherche intelligente dans l’Assistant **Implémenter MonoBehavior** .

    -   Prise en charge de l’affichage contextuel dans les Assistants (par exemple, les messages NetworkBehavior s’affichent uniquement si vous utilisez NetworkBehavior).

    -   Prise en charge supplémentaire de messages NetworkBehavior dans les Assistants.

-   **Interface utilisateur :**

    -   Ajout d’une option pour configurer la visibilité des messages MonoBehavior.

    -   Suppression des pages de propriétés de Visual Studio qui ne sont pas pertinentes pour les projets Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Génération de projet :**

    -   Correction des références à UnityEngine et UnityEditor sur Unity 4.6.

    -   Correction de la génération des fichiers projet quand Unity s’exécute sur OSX.

    -   Correction de la gestion des noms de projet contenant des caractères #.

    -   Limitation des projets générés à C# 4.

-   **Débogueur :**

    -   Correction d’un problème d’évaluation d’expression lors du débogage au sein d’une coroutine Unity.

    -   Correction d’un problème provoquant le blocage de Visual Studio pendant le débogage.

-   **Interface utilisateur :**

    -   Correction d’une incompatibilité avec l’extension [Tabs Studio](https://tabsstudio.com/) de Visual Studio.

-   **Programme d’installation :**

    -   Prise en charge de l’installation de VSTU au niveau de la machine (installation pour tous les utilisateurs) en créant des entrées de Registre HKLM.

    -   Correction des problèmes de désinstallation de VSTU quand la même version de VSTU est installée pour plusieurs versions différentes de Visual Studio. C’est le cas, par exemple, quand VSTU **2015** 2.1.0.0 et VSTU **2013** 2.1.0.0 ont été installés ensemble.

## <a name="21"></a>2.1
 Publication 08-09-2015

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge d’Unity 5.2

### <a name="bug-fixes"></a>Correctifs de bogues

-   Afficher les éléments de menu sur Unity < 4.2

-   Un message d’erreur n’est plus affiché quand Visual Studio verrouille les fichiers XML intellisense.

-   Gérer les points d’arrêt conditionnels <\<When Changed>> quand l’argument conditionnel n’est pas une valeur booléenne.

-   Correction des références aux assemblys UnityEngine et UnityEditor pour les applications du Windows Store.

-   Correction de l’erreur lors de l’exécution pas à pas dans le débogueur : Impossible de parcourir, exception générale.

-   Correction du nombre d’accès des points d’arrêt dans Visual Studio 2015.

## <a name="20"></a>2.0
 Publication 20-07-2015

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Intégration Unity :**

    -   Correction de la conversion de symboles de débogage créés avec Visual Studio 2015 lors de l’importation d’une DLL et de ses symboles de débogage (PDB).

    -   Toujours générer des fichiers MDB lors de l’importation d’une DLL et de ses symboles de débogage (PDB), sauf quand un fichier MDB est également fourni.

    -   Correction de la pollution du répertoire du projet Unity avec un répertoire obj.

    -   Correction de la génération des références à System.Xml.Link et System.Runtime.Serialization.

    -   Ajout de la prise en charge de plusieurs abonnés aux raccordements API pour la génération du fichier projet.

    -   Toujours terminer la génération du fichier projet même quand l’un des fichiers à générer est verrouillé.

    -   Ajout de la prise en charge des caractères génériques (*) dans le filtre d’extension lors de la spécification des fichiers à inclure dans le projet C#.

-   **Intégration Visual Studio :**

    -   Correction d’un problème de compatibilité avec Productivity Power Tools.

    -   Correction de la génération de MonoBehaviors autour des déclarations d’événements et de délégués.

-   **Débogueur :**

    -   Correction d’un blocage potentiel lors du débogage.

    -   Correction d’un problème où les variables locales ne s’affichent pas dans certains frames de pile.

    -   Correction de l’inspection des tableaux vides.

## <a name="20-preview-2"></a>2.0 Preview 2
 Publication 02-04-2015

### <a name="new-features"></a>Nouvelles fonctionnalités

-   **Explorateur de projets Unity :**

    -   Renommer automatiquement la classe lorsque vous renommez un fichier dans l’Explorateur de projets Unity (voir la boîte de dialogue **Options** ).

    -   Sélectionner automatiquement les scripts nouvellement créés dans l’Explorateur de projets Unity.

    -   Suivre le script actif dans l’Explorateur de projets Unity (voir la boîte de dialogue **Options** ).

    -   Procéder à une synchronisation double de l’Explorateur de solutions Visual Studio (voir la boîte de dialogue **Options** ).

    -   Adopter les icônes de Visual Studio dans le projet Unity.

-   **Débogueur :**

    -   Sélectionner la cible de débogage active à partir d’une liste de cibles de débogage enregistrées ou récemment utilisées (voir la boîte de dialogue **Options** ).

    -   Créer des points d’arrêt sur fonction sur les méthodes MonoBehavior et appliquez-les à plusieurs classes MonoBehavior.

    -   Prendre en charge Générer l’ID de l’objet dans le débogueur.

    -   Prendre en charge le nombre d’accès à un point d’arrêt dans le débogueur.

    -   Prendre en charge l’exception sur point d’arrêt dans le débogueur (à titre expérimental. voir la boîte de dialogue **Options** ).

    -   Prendre en charge la création d’objets et de tableaux lors de l’évaluation d’expressions dans le débogueur.

    -   Prendre en charge la comparaison de valeurs null lors des expressions d’évaluation dans le débogueur.

    -   Filtrer les membres obsolètes dans les fenêtres Espion du débogueur.

-   **Programme d’installation :**

    -   Inscription optimisée de l’extension Visual Studio Tools pour Unity.

    -   Installer le package Visual Studio Tools pour Unity pour Unity 5.

-   **Documentation :** Améliorer les performances de la génération de la documentation.

-   **Assistants :** Prise en charge de nouvelles méthodes MonoBehavior pour Unity 4.6 et Unity 5.

-   **Unity :** Indicateurs de recherche non sécurisés et définitions personnalisées dans les fichiers .rsp pendant la génération du fichier projet.

-   **Interface utilisateur :** Ajout de la boîte de dialogue **Options** des Outils Visual Studio pour Unity dans Visual Studio.

### <a name="bug-fixes"></a>Correctifs de bogues

-   **Explorateur de projets Unity :**

    -   Actualiser l’Explorateur de projets Unity après que les fichiers sont déplacés ou renommés à partir de l’Explorateur de solutions Visual Studio.

    -   Conserver les sélections lorsque vous renommez des fichiers dans l’Explorateur de projets Unity.

    -   Empêcher le développement / la réduction automatique lorsque l’utilisateur double-clique sur les fichiers dans l’Explorateur de projets Unity.

    -   S’assurer que les fichiers nouvellement sélectionnés sont visibles dans l’Explorateur de projets Unity.

-   **Débogueur :**

    -   Éviter un éventuel blocage de Visual Studio lors de l’évaluation des expressions dans le débogueur.

    -   S’assurer que les appels de méthode s’exécutent sur le domaine approprié dans le débogueur.

-   **Unity :**

    -   Corriger l’emplacement d’UnityVS.OpenFile avec Unity 5.

    -   Corriger l’emplacement de pdb2mdb avec Unity 5.

    -   Empêcher une possible exception pendant la génération du fichier projet.

    -   Éviter un blocage possible lors de l’exécution d’Unity sur OSX.

    -   Gérer les exceptions internes.

    -   Envoyer les journaux de console Unity à la liste d’erreurs Visual Studio.

-   **Documentation :** Corriger la génération de la documentation pour la nouvelle documentation Unity.

-   **Projet :** Déplacer et renommer les fichiers .meta Unity si nécessaire, même dans les dossiers.

-   **Assistants :** Corriger l’ordre des paramètres de la méthode MonoBehavior lors de la génération de code.

-   **Interface utilisateur :** Prendre en charge les thèmes Visual Studio pour les icônes et le menu contextuel.

## <a name="20-preview"></a>2.0 Preview
 Publication 12-11-2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge de Visual Studio 2015.

-   Coloration du code pour les nuanceurs Unity dans Visual Studio 2015.

-   Visualisation améliorée des valeurs lors du débogage.

    -   Meilleure visualisation des ArrayLists, des listes, des tables de hachage et des dictionnaires.

    -   Afficher les membres non publics et les membres statiques en tant que catégories dans les vues espion et les vues locales.

    -   Affichage amélioré de SerializedProperty d’Unity pour évaluer uniquement le champ de valeur valide pour la propriété.

    -   Prise en charge de DebuggerDisplayAttribute pour les classes et les structs.

    -   Prise en charge de DebuggerTypeProxyAttribute support.

-   Effectuer l’insertion des méthodes MonoBehaviour à l’aide de nos assistants afin de respecter les conventions de codage des utilisateurs.

-   Implémenter la prise en charge des modèles de texte au moment de la compilation dans les projets UnityVS générés.

-   Implémenter la prise en charge des ressources ResX dans les projets UnityVS générés.

-   Prendre en charge l’ouverture des nuanceurs dans Visual Studio à partir d’Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Nettoyage des sockets avant le démarrage du jeu dans Unity après le déclenchement de l’attachement et de la lecture dans Visual Studio. Cela résout certains problèmes de stabilité de la connexion entre Unity et VS lors de l’utilisation de l’attachement et de la lecture.

-   Éviter l’appeler de méthodes dans l’interface du débogueur du moteur de script Unity qui sont enclines à figer Unity. Cela résout le blocage d’Unity lors de l’attachement du débogueur.

-   Résolution de l’affichage des piles d’appel quand aucun symbole n’est disponible.

-   Ne pas enregistrer le rappel du journal si ce n’est pas nécessaire.

## <a name="192"></a>1.9.2
 Publication 09-10-2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Améliorer la détection des joueurs Unity.

-   Lorsque vous utilisez notre ouvreur de fichiers, faites passer à Unity le numéro de ligne, ainsi que le nom du fichier.

-   Documentation Unity en ligne par défaut s’il n’existe aucune documentation locale.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger les incidents Unity potentiels lors de l’atteinte d’un point d’arrêt après rechargement d’un domaine.

-   Résoudre les exceptions affichées dans la console Unity lors de la fermeture de nos fenêtres Configuration ou About, après rechargement d’un domaine.

-   Corriger la détection des versions Unity 64 bits exécutées localement.

-   Corriger le filtrage des MonoBehaviours par version Unity dans les Assistants.

-   Fix bug where all assets were included in the project files if the extension filter was empty.

## <a name="191"></a>1.9.1
 Publication 22-09-2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Optimiser le point d’arrêt de la liaison vers les emplacements source.

-   Prise en charge des méthodes surchargées dans l’évaluation d’expression du débogueur.

-   Prise en charge des primitives de boxing et des types de valeur dans l’évaluation d’expression du débogueur.

-   Prise en charge de la recréation de l’environnement de variables locales C# lors du débogage des méthodes anonymes.

-   Supprimer et renommer les fichiers .meta lors de la suppression ou du changement de nom des fichiers à partir de Visual Studio.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger la gestion des thèmes Visual Studio. Avant, les boîtes de dialogue de thèmes noirs pouvaient apparaître vides.

-   Correction du problème de blocage d’Unity lors de la connexion du débogueur pendant la recompilation par Unity.

-   Corriger les points d’arrêt lors du débogage à distance des éditeurs ou des lecteurs compilés sur un autre système.

-   Résoudre un éventuel incident Visual Studio lorsqu’un point d’arrêt est atteint.

-   Corriger la liaison des points d’arrêt afin d’éviter que les points d’arrêt ne s’affichent comme déchargés.

-   Corriger la gestion de la portée des variables dans le débogueur pour éviter que des variables en direct n’apparaissent hors de portée.

-   Correction du problème de la recherche de membres statiques dans l’évaluation d’expression du débogueur.

-   Corriger l’affichage des types dans l’évaluation d’expression du débogueur pour afficher les propriétés et les champs statiques.

-   Corriger la génération de solution lorsque les noms de projet Unity incluent des caractères spéciaux que Visual Studio interdit (problème de connexion #948666).

-   Corriger le package Visual Studio Tools Unity pour arrêter immédiatement l’envoi d’événements à la console après que l’option a été désactivée (problème de connexion #933357).

-   Corriger la détection de références pour régénérer correctement les références aux nouvelles API comme UnityEngine.UI dans les projets générés par UnityVS.

-   Corriger le programme d’installation pour exiger que Visual Studio se ferme avant l’installation afin d’éviter des installations corrompues.

-   Corriger le programme d’installation pour installer les assemblys de référence Unity comme composants autonomes, partagés entre toutes les versions de VSTU.

-   Corriger l’ouverture de scripts avec VSTU dans les versions 64 bits d’Unity.

## <a name="19"></a>1.9
 Publication 29-07-2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Dans la fenêtre Attacher le débogueur Unity, ajoutez la possibilité d’entrer un port et une adresse IP personnalisés pour le débogage.

-   Ajouter l’option de configuration pour définir que Unity s’exécute en arrière-plan ou non.

-   Ajouter l’option de configuration pour générer les fichiers solution et projet ou uniquement les fichiers projet.

-   Cible de démarrage : choisir Attacher à Unity ou Attacher à Unity et lire.

-   Affichage de tableaux multidimensionnels dans le débogueur.

-   Gérer les nouveaux ports de débogage du lecteur Unity.

-   Gérer les références aux nouveaux assemblys Unity comme les assemblys GUI 4.6 d’Unity.

-   Déconstruit les fermetures pour afficher correctement les variables locales lors du débogage.

-   Déconstruit les variables générées des itérateurs en arguments lors du débogage.

-   Conserver l’état de l’Explorateur de projet Unity après rechargement d’un projet.

-   Ajouter une commande pour synchroniser l’Explorateur de projets Unity avec le document en cours.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger les points d’arrêt conditionnels dont les conditions sont définies avant le démarrage du débogueur.

-   Résoudre les références à UnityEngine afin d’éviter des avertissements.

-   Résolution de l’analyse des versions pour les versions Unity bêta.

-   Corriger le problème où les variables n’apparaissent pas dans la fenêtre de variables locales lors de l’atteinte d’un point d’arrêt ou du parcours pas à pas.

-   Corriger les info-bulles des variables dans Visual Studio 2013.

-   Corriger la génération de la documentation IntelliSense pour Unity 4.5.

-   Corriger la communication Unity / Visual Studio après le rechargement d’un domaine (lire/arrêter dans Unity).

-   Corriger la gestion des composants dans les thèmes Visual Studio.

> [!IMPORTANT]
>  C# étant le langage prédominant de l’écosystème Unity - les nouvelles ressources d’exemples sont en C#, la documentation Unity sera par défaut en C# -, nous avons supprimé notre support de base pour UnityScript et pour Boo afin de mieux se concentrer sur l’expérience C#. Par conséquent, les solutions VSTU sont désormais en C# uniquement et beaucoup plus rapides à charger.

## <a name="182"></a>1.8.2
 Publication 07-01-2014

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Contourner un problème dans la couche réseau du moteur de script de Unity sur Mavericks pour la découverte à distance d’éditeurs.

-   Gérer les nouveaux ports pour découvrir les lecteurs Unity à distance.

-   Référencer l’assembly UnityEngine spécifique à la cible de génération en cours.

-   Ajouter le paramètre pour filtrer les fichiers à inclure dans les projets générés.

-   Ajouter le paramètre pour désactiver l’envoi de journaux de console à la liste d’erreurs Visual Studio. Cela est utile si vous utilisez PlayMaker ou Console Pro, car il peut n’y avoir qu’un seul rappel enregistré dans Unity pour recevoir des journaux de la console.

-   Ajouter le paramètre pour désactiver la génération des symboles de débogage mdb. Cette option est utile si vous générez la mdb vous-même.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Corriger une régression lorsque les fichiers ouverts dans Visual Studio à partir de Unity > = 4.2 perdraient IntelliSense.

-   Corriger les boîtes de dialogue Visual Studio pour gérer les thèmes personnalisés.

-   Corriger la fermeture du menu contextuel de l’UPE.

-   Empêcher un incident dans Unity lorsque l’assembly généré spécifique à la version est désynchronisé.

## <a name="181"></a>1.8.1
 Publication 21-11-2013

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Ajustement des Assistants MonoBehaviour avec les API Unity 4.3.

-   Les Assistants MonoBehaviour filtrent les API Unity selon la version que vous utilisez.

-   Ajouter une référence à System.Xml.Linq aux projets de Unity > 4.1.

-   Agrémenter les appels à Debug.Log pour ne pas inclure le début du Stack Trace dans le message.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction d’un bogue dans lequel nous interférons avec la gestion par défaut des fichiers JavaScript dans Visual Studio.

-   Correction du pixel blanc apparaissant dans Visual Studio, en vrai cette fois.

-   Correction de la suppression de l’assembly UnityVS.VersionSpecific s’il est marquée en lecture seule par un SCM.

-   Fixed exceptions when creating sockets in the UnityVS package.

-   Correction d’un incident dans Visual Studio lors du chargement d’images en stock à partir d’assemblys Visual Studio.

-   Correction d’un bogue dans la génération d’UnityVS.VersionSpecific pour les générations de code source d’Unity.

-   Correction d’un blocage possible lors de l’ouverture d’un socket dans le package Unity.

-   Correction de la gestion du projet Unity avec un tiret (-) dans le nom.

-   Correction des scripts d’ouverture d’Unity à ne pas confondre pas la commande ALT+TAB pour Unity 4.2 et versions ultérieures.

## <a name="180"></a>1.8.0
 Publication 24-09-2013

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Amélioration spectaculaire de la vitesse de connexion du débogueur.

-   Gestion automatique de la navigation vers un fichier et une ligne dans Unity 4.2 et versions ultérieures.

-   Points d’arrêt conditionnels.

-   Le générateur de fichiers de projet gère désormais les modèles T4.

-   Mettre à jour les Assistants MonBehavior avec les nouvelles API.

-   Intellisense documentation in C# for Unity types.

-   Évaluation des expressions arithmétiques et logiques.

-   Meilleure découverte des éditeurs distants pour l’aperçu de débogage distant.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction d’un bogue avec fuite d’un thread dans Visual Studio après déconnexion du débogueur.

-   Correction d’un pixel blanc apparaissant dans Visual Studio.

-   Correction de la gestion des clics sur l’icône de barre d’état.

-   Correction de la génération des références avec les assemblys des dossiers Plugins.

-   Correction de la création de sockets à partir du package UnityVS en cas d’exceptions.

-   Correction de la détection de nouvelles versions d’UnityVS.

-   Correction de l’invite du Gestionnaire de licences lors de l’expiration de la licence.

-   Correction d’un bogue qui peut afficher vide la liste des processus dans la fenêtre de l’attachement du débogueur au processus de Visual Studio.

-   Correction de la modification des valeurs booléennes dans la vue locale.

## <a name="122"></a>1.2.2
 Publication 09-07-2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Gérer les noms complets dans l’évaluateur d’expression.

-   Correction d’un blocage lié à la gestion des exceptions où le moteur de script Unity envoie des données incorrectes de StackFrame.

-   Correction du processus de génération pour les cibles du Web.

-   Correction d’une erreur susceptible de se produire si Visual Studio a été démarré et qu’un fichier supprimé se trouvait dans la liste des fichiers à ouvrir au démarrage.

-   Correction d’UnityVS.OpenFile pour gérer les fichiers autres que les fichiers script, comme les nuanceurs compilés.

-   Il est maintenant fait référence à Boo.Lang et UnityScript.Lang à partir de tous les projets C#.

-   Correction de la génération des références dans les projets si le projet comporte des caractères spéciaux.

-   Contournement d’un problème VS où les appels de méthode à des projets supprimés déclenchent plusieurs zones de message NullReferenceException.

-   Correction de la gestion des assemblys de la version bêta Unity 4.2.

## <a name="121"></a>1.2.1
 Publication 09-04-2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction du déploiement local des assemblys Unity pour l’exécution de code en cas d’erreur d’E/S (telle que fichiers en lecture seule ou fichiers verrouillés par Visual Studio).

-   Correction d’une régression où de l’ouverture d’un script à partir d’Unity ne traiterait pas le fichier s’il était déjà ouvert dans Visual Studio.

-   Correction de problème de performances de la nouvelle gestion des exceptions.

-   Correction de la liaison des points d’arrêt dans certaines DLL externes.

## <a name="12"></a>1.2
 Publication 25-03-2013

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Amélioration spectaculaire de la vitesse de connexion du débogueur.

-   Explorateur de projets Unity optimisé pour les grands projets.

-   Respecte les paramètres de Visual Studio pour interrompre (ou pas) géré et les exceptions non gérées.

-   Respecte le paramètre de Visual Studio pour l’appel de ToString sur les variables locales.

-   Ajouter un nouveau menu Débogage -> Attacher le débogueur Unity, que vous pouvez utiliser pour déboguer les lecteurs Unity.

-   Conserver les projets personnalisés ajoutés à la solution UnityVS lors de la génération du fichier solution.

-   Ajouter nouveau raccourci clavier CTRL+ ALT M -> CTRL+H pour afficher la documentation Unity pour la fonction Unity ou un membre à la position du point d’insertion.

-   Prendre les fichiers de réponse du compilateur (rsp) en compte lors de la compilation à partir de Visual Studio.

-   Décomposer les types générés par le compilateur pour afficher les variables lorsque vous déboguez des méthodes de générateur.

-   Simplifier le débogage à distance en supprimant la nécessité de configurer un dossier partagé sur Unity. Maintenant, vous devez simplement avoir accès à votre projet Unity à partir de Windows.

-   Installer un profil Unity personnalisé comme profil cible .net standard. Corrige tous les faux positifs que ReSharper peut afficher.

-   Contourner un bogue du moteur de script Unity, afin que le débogueur ne s’arrête pas sur les threads non correctement inscrits.

-   Correction de l’ouverture de fichier pour éviter une condition de concurrence dans Visual Studio où il est dit qu’il est possible d’ouvrir les fichiers et qu’un incident se produit à la demande d’ouverture.

-   UnityVS demande maintenant d’actualiser la build lorsque Visual Studio génère le projet, et non plus lors de l’enregistrement du fichier.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction de notre profil .net personnalisé

-   Correction de l’intégration de thèmes, qui résout les problèmes avec le thème foncé Visual Studio 2012.

-   Correction du raccourci de comportement rapide dans Visual Studio 2012.

-   Correction d’un problème de pas à pas qui peut se produire lors du débogage et qu’un thread non principal atteint un point d’arrêt.

-   Correction de l’achèvement UnityScript et Boo des alias de type, tel qu’int.

-   Correction d’exception lors de l’écriture d’une nouvelle chaîne UnityScript ou Boo.

-   Correction des exceptions dans les menus Unity lorsqu’une solution n’a pas été chargée.

-   Correctif de bogue UVS-48 : la saisie de guillemets doubles produit parfois des erreurs et arrête toutes les fonctions (exécution de code, mise en surbrillance de la syntaxe, etc.).

-   Résolution de bogue UVS-46 : Duplication du fichier de script ouvert (UnityScript) quand vous cliquez sur la liste d’erreurs de Visual Studio.

-   Résolution de bogue UVS-42 : Le logo de connectivité Unity dans la barre d’état ne traite pas les événements de souris dans Visual Studio 2012.

-   Résolution de bogue UVS-44 : La combinaison Ctrl+Maj+Q n’est pas disponible dans Visual Studio 2012 pour les MonoBehaviours rapides.

-   Résolution de bogue UVS-40 : Les éléments sélectionnés dans l’Explorateur de projets Unity sont illisibles quand la fenêtre est inactive dans le thème « foncé » de Visual Studio 2012.

-   Résolution de bogue UVS-39 : Problème de création de jetons pour les chaînes d’échappement.

-   Résolution de bogue UVS-35 : Appel de ToString sur des objets durant l’inspection de variables.

-   Résolution de bogue UVS-27 : Incohérence de la fenêtre Aller au symbole avec le thème « foncé » dans Visual Studio 2012.

-   Résolution de bogue UVS-11 : Variables locales dans les coroutines.

## <a name="11--beta-release"></a>1.1 – Version bêta
 Publication 09-10-2014

## <a name="1013"></a>1.0.13
 Publication 21-01-2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction d’un blocage de Visual Studio qui peut se produire si le programme débogué cible envoie des événements de thread non valides. Cela se produit généralement lors du débogage d’un Unity distant sur OSX.

-   Correction d’une recherche Visual Studio qui peut se produire si une exception arrête le débogueur.

-   Correction des programmes d’assistance MonoBehavior lorsqu’un MonoBehavior C# figure dans un espace de noms.

-   Correction des info-bulles du débogueur pour UnityScript dans Visual Studio 2012.

-   Correction de la génération de projet lorsque seules les constantes de débogage sont modifiés à partir d’Unity.

-   Correction de la navigation au clavier dans l’Explorateur de projets Unity.

-   Correction de la colorisation UnityScript pour les chaînes d’échappement.

-   Correction de l’ouvreur de fichiers pour mieux deviner le nom du projet en cas d’utilisation en dehors d’Unity. Cela est nécessaire lorsque l’utilisateur utilise un ouvreur de fichiers tiers dans Unity qui délègue à UnityVS.

-   Correction de la gestion de longs messages envoyés d’Unity à UnityVS. Avant cela, les longs messages pouvaient bloquer la partie messagerie d’UnityVS. Par conséquent, il arrivait que UnityVS ne puisse pas ouvrir un fichier à partir d’Unity.

## <a name="1012"></a>1.0.12
 Publication 03-01-2013

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction du verrouillage de Visual Studio qui peut se produire lorsque Visual Studio supprime un point d’arrêt.

-   Correction d’un bogue dans lequel certains points d’arrêt ne sont pas atteints après que Unity a recompilé les scripts de jeu.

-   Correction du débogueur pour informer correctement Visual Studio lorsque des points d’arrêt ont été séparés.

-   Correction d’un problème d’enregistrement susceptible d’empêcher le débogueur Visual Studio de déboguer les programmes natifs.

-   Correction d’une exception susceptible de se produire lors de l’évaluation d’expressions UnityScript et Boo.

-   Correction d’une régression dans laquelle la modification du niveau de l’API .NET dans Unity ne déclenche pas une mise à jour des fichiers projet.

-   Correction d’un problème d’API où le code utilisateur ne peut participer au Gestionnaire de rappel du journal.

## <a name="1011"></a>1.0.11
 Publication 28-11-2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge officielle de Unity 4.

-   Manipulation des scripts à partir de l’Explorateur de projets Unity.

-   Intégration dans la fenêtre Naviguer vers de Visual Studio.

-   Analyse du message de la console Info, afin qu’un clic sur la liste d’erreurs vous permette d’accéder à la première StackFrame avec symboles.

-   Ajouter une [API](../cross-platform/customize-project-files-created-by-vstu.md) pour permettre à utilisateur de participer à la génération du projet.

-   Ajouter une [API](../cross-platform/share-the-unity-log-callback-with-vstu.md) pour permettre à utilisateur de participer au rappel de journal.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction de la régression dans l’arrière-plan de l’Explorateur de projets Unity dans Visual Studio 2012.

-   Correction de la génération de projet pour les utilisateurs du profil .net complet.

-   Correction de la génération de projet pour les utilisateurs de la cible Web.

-   Correction de la génération de projet pour inclure les symboles de compilation DEBUG et TRACE comme le fait Unity.

-   Correction d’incident lors de l’utilisation de caractères spéciaux dans la fenêtre Accéder au symbole.

-   Correction du problème s’il n’est pas possible d’injecter notre icône dans la barre d’état de Visual Studio.

## <a name="1010"></a>1.0.10
 Publication 09-10-2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Correction de l’arrière-plan de l’Explorateur de projets Unity dans Visual Studio 2010.

-   Correction d’un blocage de Visual Studio qui peut se produire si UnityVS a tenté d’attacher le débogueur à instance Unity dont l’interface du débogueur s’est précédemment bloquée.

-   Résolution d’un blocage de Visual Studio qui peut se produire quand un point d’arrêt a été défini et qu’un rechargement d’AppDomain a lieu.

-   Résolution de la façon d’extraire des assemblys d’Unity pour éviter le verrouillage des fichiers et confondre le processus de génération d’Unity.

## <a name="109"></a>1.0.9
 Publication 03-10-2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération de projet lorsque le projet Unity inclut les ressources JavaScript réelles.

-   Résolution de la gestion des erreurs dans l’évaluation d’expression.

-   Résolution de la définition de nouvelles valeurs en champs de types valeur.

-   Résolution des effets secondaires éventuels lorsque vous pointez sur des expressions à partir de l’éditeur de code.

-   Résolution de la façon dont les types sont recherchés dans les assemblys chargés pour l’évaluation d’expression.

-   Résolution de bogue UVS-21 : L’évaluation de l’affectation sur les objets Unity n’a aucun effet.

-   Résolution de bogue UVS-21 : Pointeur non valide durant l’évaluation d’un appel de méthode à l’API Math Unity.

## <a name="108"></a>1.0.8
 Publication 26-09-2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la façon dont notre ouvreur de script a acquis le chemin d’accès au projet pour s’assurer qu’il peut ouvrir Visual Studio et les scripts.

-   Résolution d’un bogue avec les points d’arrêt créés pendant que la session de débogage était en cours d’exécution et entraînait le verrouillage de Visual Studio.

-   Résolution de la façon dont UnityVS est enregistré sur Visual Studio 2010.

## <a name="107"></a>1.0.7
 Publication 14-09-2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge de Visual Studio 2012.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération des fichiers de projet de plug-ins et d’éditeur pour correspondre au comportement d’Unity.

-   Résolution de la traduction de symboles .pdb sur Unity 4.

> [!IMPORTANT]
>  En raison de la prise en charge de Visual Studio 2012, nous avons dû renommer quelques fichiers et déplacer d’autres. Le package UnityVS pour importer Unity est maintenant appelé UnityVS 2010 ou UnityVS 2012, pour, respectivement, Visual Studio 2010 et Visual Studio 2012. Cette version requiert également que les fichiers de projet UnityVS soient régénérés.

## <a name="106---internal-build"></a>1.0.6 - version interne
 Publication 12-09-2012

## <a name="105"></a>1.0.5
 Publication 10-09-2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération des fichiers projet lorsque les scripts ou les nuanceurs ont un caractère xml non valide.

-   Résolution de la détection d’instances Unity quand Unity a été connecté au serveur de ressources. Cela s’est traduit par un échec à l’ouverture de fichiers à partir de Unity et de la connexion automatique du débogueur Visual Studio.

## <a name="104"></a>1.0.4
 Publication 05-09-2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Conversion automatique des symboles de débogage dans Unity.

     Si vous avez un assembly .dll .NET avec son .pdb associé dans votre dossier Composants, réimportez simplement l’assembly et UnityVS convertira le fichier .pdb en un fichier de symboles de débogage que le moteur de script d’Unity comprend, et vous pourrez effectuer un pas à pas détaillé dans vos assemblys .NET à partir de UnityVS.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de l’incident UnityVS lors du débogage provoqué par les exceptions levées par des méthodes ou propriétés à l’intérieur d’Unity.

## <a name="103"></a>1.0.3
 Publication 04-09-2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Nouvelle option de configuration pour désactiver l’utilisation d’UnityVS pour ouvrir des fichiers à partir d’Unity.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de la génération des références à UnityEditor pour les projets autres que les projets éditeur.

-   Résolution de la définition du symbole UNITY_EDITOR pour les projets non éditeur.

-   Résolution des pannes VS aléatoires causés par notre barre d’état personnalisé.

## <a name="102"></a>1.0.2
 Publication 30-08-2012

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution du Conflit avec le débogueur PythonTools.

-   Résolution des références à Mono.Cecil.

-   Résolution du bogue dans la façon dont les scripts des assemblys ont été extraits d’Unity avec Unity 4 b7.

## <a name="101"></a>1.0.1
 Publication 28-08-2012

### <a name="new-features"></a>Nouvelles fonctionnalités

-   Prise en charge de l’aperçu pour la version Unity 4.0 bêta.

### <a name="bug-fixes"></a>Correctifs de bogues

-   Résolution de l’inspection des propriétés levant des exceptions.

-   Résolution de la descente dans les objets de base lors de l’inspection des objets.

-   Résolution de liste déroulante vide pour le point d’insertion dans l’Assistant MonoBehavior.

-   Résolution de l’exécution de la DLL dans le dossier Ressources pour UnityScript et Boo.

## <a name="10--initial-release"></a>1.0 – Version initiale
 Publication 22-08-2012
