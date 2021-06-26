---
title: Utiliser les fenêtres d’outils pour afficher la structure du code
description: Découvrez comment utiliser les fenêtres outil Affichage de classes, hiérarchie d’appels, Explorateur d’objets et définition de code (C++ uniquement) pour examiner les classes et leurs membres dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/19/2019
ms.topic: reference
f1_keywords:
- vs.documentoutline.window
- vs.classview
- VS.CodeDefinitionView
- VS.CodeDefinitionWindow
- vs.componentpicker
- vs.callbrowser
helpviewer_keywords:
- document outline window
- Visual Studio, object browser
- call hierarchy
- Visual Studio, document outline window
- code definition window [Visual Studio]
- Visual Studio, class view
- Visual Studio, call hierarchy window
- class view
- object browser
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 41c11025e22c1288387862fa138b35efbbca8557
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924953"
---
# <a name="view-the-structure-of-code-by-using-different-tool-windows"></a>Afficher la structure du code à l’aide de différentes fenêtres outil

Vous pouvez examiner les classes et leurs membres dans Visual Studio à l’aide de différentes fenêtres d’outils, y compris **Affichage des classes**, **Hiérarchie d’appels**, **Explorateur d’objets** et **Définition de code** (C++ uniquement). Ces fenêtres d’outils peuvent examiner du code dans des projets Visual Studio, des composants .NET, des composants COM, des bibliothèques de liens dynamiques (DLL) et des bibliothèques de types (TLB).

Vous pouvez également utiliser l’**Explorateur de solutions** pour parcourir les types et les membres dans vos projets, rechercher des symboles, afficher la hiérarchie d’appels d’une méthode, rechercher les références des symboles, etc., sans avoir à basculer entre plusieurs fenêtres d’outils.

Si vous avez l’édition Visual Studio Enterprise, vous pouvez utiliser les *cartes de code* pour visualiser la structure de votre code et ses dépendances sur l’ensemble de la solution. Pour plus d’informations, consultez [Mapper les dépendances avec des cartes de code](../modeling/map-dependencies-across-your-solutions.md).

## <a name="class-view-visual-basic-c-c"></a>Affichage de classes (Visual Basic, C#, C++)

L’**affichage de classes** est illustré dans le cadre de l’**Explorateur de solutions** et dans une fenêtre distincte. **Affichage de classes** présente les éléments d’une application. Le volet supérieur affiche les espaces de noms, les types, les interfaces, les énumérations et les classes, alors que le volet inférieur affiche les membres qui appartiennent au type sélectionné dans le volet supérieur. Cette fenêtre vous permet d’accéder aux définitions des membres dans le code source (ou dans l’**Explorateur d’objets** si l’élément est défini en dehors de votre solution).

Il est inutile de compiler un projet pour afficher ses éléments dans la fenêtre **Affichage de classes**. La fenêtre est actualisée quand vous modifiez le code dans votre projet.

Vous pouvez ajouter du code à votre projet en sélectionnant le nœud du projet et en choisissant le bouton **Ajouter** pour ouvrir la boîte de dialogue **Ajouter un nouvel élément**. Le code est ajouté dans un fichier distinct.

Si votre projet est archivé dans le contrôle de code source, chaque élément **Affichage de classes** affiche une icône qui indique l’état du code source du fichier. Les commandes de contrôle de code source courantes, comme **Extraire**, **Archiver** et **Obtenir la dernière version**, sont également disponibles dans le menu contextuel de l’élément.

### <a name="class-view-toolbar"></a>Barre d’outils Affichage de classes

La barre d’outils **affichage de classes** contient les commandes suivantes :

|Nom|Description|
|-|-|
|**Nouveau dossier**|Crée un dossier ou sous-dossier virtuel dans lequel vous pouvez organiser les éléments fréquemment utilisés. Elles sont enregistrées dans le fichier de solution active (*. suo*). Une fois que vous avez renommé ou supprimé un élément dans votre code, il peut apparaître dans un dossier virtuel en tant que nœud d'erreur. Pour corriger ce problème, supprimez le nœud d'erreur. Si vous avez renommé un élément, vous pouvez le déplacer de nouveau de la hiérarchie de projet vers le dossier.|
|**Précédent**|Permet d'accéder à l'élément précédemment sélectionné.|
|**Prédictif**|Permet d'accéder à l'élément sélectionné suivant.|
|**Afficher le diagramme de classes** (projets de code managé uniquement)|Devient disponible quand vous sélectionnez un espace de noms ou un type dans **Affichage de classes**. Quand un espace de noms est sélectionné, le diagramme de classes affiche tous les types qu'il contient. Quand un type est sélectionné, le diagramme de classes affiche uniquement ce type.|

### <a name="class-view-settings"></a>Paramètres de l’affichage de classes

Le bouton **paramètres de affichage de classes** de la barre d’outils contient les paramètres suivants :

|Nom|Description|
|-|-|
|**Afficher les types de base**|Les types de base sont affichés.|
|**Afficher les références de projet**|Les références de projet sont affichées.|
|**Afficher les types et les membres masqués**|Les types et membres masqués (non prévus pour être utilisés par les clients) sont affichés en gris clair.|
|**Afficher les membres publics**|Les membres publics sont affichés.|
|**Afficher les membres protégés**|Les membres protégés sont affichés.|
|**Afficher les membres privés**|Les membres privés sont affichés.|
|**Afficher les autres membres**|D'autres types de membres sont affichés, y compris les membres internes (ou Friend en Visual Basic).|
|**Afficher les membres hérités**|Les membres hérités sont affichés.|

### <a name="class-view-shortcut-menu"></a>Menu contextuel de la fenêtre Affichage de classes

Le menu contextuel (ou clic droit) de **affichage de classes** peut contenir les commandes suivantes, selon le type de projet sélectionné :

|Nom|Description|
|-|-|
|**Atteindre la définition**|Recherche la définition de l’élément dans le code source ou dans l’**Explorateur d’objets** si l’élément n’est pas défini dans le projet ouvert.|
|**Parcourir les définitions**|Affiche l’élément sélectionné dans l’**Explorateur d’objets**.|
|**Rechercher toutes les références**|Recherche l’élément de l’objet actuellement sélectionné et affiche les résultats dans une fenêtre **Résultats de la recherche**.|
|**Appliquer le filtre au type** (code managé uniquement)|Affiche uniquement le type ou l'espace de noms sélectionné. Vous pouvez supprimer le filtre en choisissant le bouton **effacer la recherche** (**X**) en regard de la zone **Rechercher** .|
|**Copy**|Copie le nom qualifié complet de l'élément.|
|**Trier par ordre alphabétique**|Répertorie les types et les membres dans l'ordre alphabétique par nom.|
|**Trier les membres par type**|Répertorie les types et les membres dans l'ordre par type (de sorte que les classes précèdent les interfaces, les interfaces précèdent les délégués et les méthodes précèdent les propriétés).|
|**Trier les membres par accès**|Répertorie les types et les membres dans l'ordre par type d'accès, tel que public ou privé.|
|**Grouper par type de membre**|Trie les types et les membres en groupes par type d'objet.|
|**Atteindre la déclaration** (code C++ uniquement)|Affiche la déclaration du type ou du membre dans le code source, si elle est disponible.|
|**Atteindre la définition**|Affiche la définition du type ou du membre dans le code source, si elle est disponible.|
|**Atteindre la référence**|Affiche une référence au type ou au membre dans le code source, si elle est disponible.|
|**Afficher la hiérarchie d’appels**|Affiche la méthode sélectionnée dans la fenêtre **Hiérarchie d’appels**.|

## <a name="call-hierarchy-window-visual-basic-c-c"></a>Fenêtre Hiérarchie d’appels (Visual Basic, C#, C++)

La fenêtre **Hiérarchie d’appels** indique où une méthode ou une propriété est appelée. Elle répertorie également les méthodes appelées à partir de cette méthode. Vous pouvez afficher plusieurs niveaux du graphique des appels, qui montre les relations appelant/appelé parmi les méthodes dans une portée spécifiée.

Vous pouvez afficher la fenêtre **Hiérarchie d’appels** en sélectionnant une méthode (ou une propriété ou un constructeur) dans l’éditeur, puis en choisissant **Afficher la hiérarchie d’appels** dans le menu contextuel. L'affichage doit ressembler à l’image suivante :

![Fenêtre Hiérarchie d’appels dans Visual Studio](../ide/media/multiplenodes.png)

La liste déroulante de la barre d’outils vous permet de spécifier la portée de la hiérarchie : la solution, le projet actuel ou le document actif.

Le volet principal affiche les appels en direction et en provenance de la méthode, et le volet **Sites d’appel** affiche l’emplacement de l’appel sélectionné. Pour les membres virtuels ou abstraits, un nœud **Remplace nom de méthode** apparaît. Pour les membres d’interface, un nœud **Implémente nom de méthode** apparaît.

La fenêtre **Hiérarchie d’appels** ne recherche pas les références au groupe de méthodes qui incluent des emplacements où une méthode est ajoutée en tant que gestionnaire d’événements ou est assignée à un délégué. Pour trouver ces références, utilisez la commande **Rechercher toutes les références**.

Le menu contextuel de la fenêtre **hiérarchie d’appels** contient les commandes suivantes :

|Nom|Description|
|-|-|
|**Ajouter comme nouvelle racine**|Ajoute le nœud sélectionné en tant que nouveau nœud racine.|
|**Supprimer racine**|Supprime le nœud racine sélectionné du volet d’arborescence.|
|**Atteindre la définition**|Navigue jusqu'à la définition d'origine d'une méthode.|
|**Rechercher toutes les références**|Recherche dans le projet toutes les références à la méthode sélectionnée.|
|**Copy**|Copie le nœud sélectionné (mais pas ses sous-nœuds).|
|**Actualiser**|Actualise les informations.|

## <a name="object-browser"></a><a name="BKMK_ObjectBrowser"></a> Explorateur d’objets

La fenêtre **Explorateur d’objets** affiche les descriptions du code dans vos projets.

Vous pouvez filtrer les composants que vous souhaitez afficher à l’aide de la liste déroulante en haut de la fenêtre. Les composants personnalisés peuvent inclure des fichiers exécutables de code managé, des assemblys de bibliothèque, des bibliothèques de types et des fichiers *. ocx* . Il n'est pas possible d'ajouter des composants personnalisés C++.

::: moniker range="vs-2017"

Les paramètres personnalisés sont enregistrés dans le répertoire d’application utilisateur Visual Studio : *%APPDATA%\Microsoft\VisualStudio\15.0\ObjBrowEX.dat*.

::: moniker-end

::: moniker range=">=vs-2019"

Les paramètres personnalisés sont enregistrés dans le répertoire d’application utilisateur Visual Studio : *%APPDATA%\Microsoft\VisualStudio\16.0\ObjBrowEX.dat*.

::: moniker-end

Le volet gauche de l’**Explorateur d’objets** montre les assemblys. Vous pouvez développer les assemblys pour afficher les espaces de noms qu’ils contiennent, puis développer les espaces de noms pour afficher les types qu’ils contiennent. Quand vous sélectionnez un type, ses membres (tels que les propriétés et les méthodes) sont répertoriés dans le volet droit. Le volet inférieur droit affiche des informations détaillées sur l'élément sélectionné.

Vous pouvez rechercher un élément spécifique à l’aide de la zone **Rechercher** en haut de la fenêtre. Les recherches ne respectent pas la casse. Les résultats de recherche sont affichés dans le volet gauche. Pour effacer une recherche, cliquez sur le bouton **effacer la recherche** (**X**) en regard de la zone de **recherche** .

L’**Explorateur d’objets** assure le suivi des sélections effectuées et vous pouvez naviguer entre vos sélections à l’aide des boutons **Suivant** et **Précédent** de la barre d’outils.

Vous pouvez utiliser l’**Explorateur d’objets** pour ajouter une référence d’assembly à une solution ouverte en sélectionnant un élément (assembly, espace de noms, type ou membre) et en choisissant le bouton **Ajouter une référence** dans la barre d’outils.

### <a name="object-browser-settings"></a>Paramètres de l’Explorateur d’objets

À l’aide du bouton Paramètres de l' **Explorateur d’objets** de la barre d’outils, vous pouvez spécifier l’une des vues suivantes :

|Nom|Description|
|-|-|
|**Afficher les espaces de noms**|Affiche les espaces de noms plutôt que les conteneurs physiques, dans le volet gauche. Les espaces de noms stockés dans plusieurs conteneurs physiques sont fusionnés.|
|**Afficher les conteneurs**|Affiche les conteneurs physiques plutôt que les espaces de noms, dans le volet gauche. **Afficher les espaces de noms** et **Afficher les conteneurs** sont des paramètres qui s’excluent mutuellement.|
|**Afficher les types de base**|Affiche les types de base.|
|**Afficher les types et les membres masqués**|Affiche les types et membres masqués (non prévus pour être utilisés par les clients) en gris clair.|
|**Afficher les membres publics**|Affiche les membres publics.|
|**Afficher les membres protégés**|Affiche les membres protégés.|
|**Afficher les membres privés**|Affiche les membres privés.|
|**Afficher les autres membres**|Affiche d'autres types de membres, y compris les membres internes (ou Friend en Visual Basic).|
|**Afficher les membres hérités**|Affiche les membres hérités.|
|**Afficher les méthodes d’extension**|Affiche les méthodes d’extension.|

### <a name="object-browser-shortcut-menu-commands"></a>Commandes du menu contextuel de l’Explorateur d’objets

Le menu contextuel (ou clic droit) dans l' **Explorateur d’objets** peut contenir les commandes suivantes, selon le type d’élément sélectionné :

|Nom|Description|
|-|-|
|**Parcourir les définitions**|Affiche le nœud principal de l'élément sélectionné.|
|**Rechercher toutes les références**|Recherche l’élément de l’objet actuellement sélectionné et affiche les résultats dans une fenêtre **Résultats de la recherche**.|
|**Appliquer le filtre au type**|Affiche uniquement le type ou l'espace de noms sélectionné. Vous pouvez supprimer le filtre en choisissant le bouton **Effacer la recherche**.|
|**Copy**|Copie le nom qualifié complet de l'élément.|
|**Remove**|Si la portée est un jeu personnalisé de composants, supprime le composant sélectionné de la portée.|
|**Trier par ordre alphabétique**|Répertorie les types et les membres dans l'ordre alphabétique par nom.|
|**Trier par type d’objet**|Répertorie les types et les membres dans l'ordre par type (de sorte que les classes précèdent les interfaces, les interfaces précèdent les délégués et les méthodes précèdent les propriétés).|
|**Trier les objets par accès**|Répertorie les types et les membres dans l'ordre par type d'accès, tel que public ou privé.|
|**Grouper par type d’objet**|Trie les types et les membres en groupes par type d'objet.|
|**Atteindre la déclaration** (projets C++ uniquement)|Affiche la déclaration du type ou du membre dans le code source, si elle est disponible.|
|**Atteindre la définition**|Affiche la définition du type ou du membre dans le code source, si elle est disponible.|
|**Atteindre la référence**|Affiche une référence au type ou au membre dans le code source, si elle est disponible.|
|**Afficher la hiérarchie d’appels**|Affiche la méthode sélectionnée dans la fenêtre **Hiérarchie d’appels**.|

## <a name="code-definition-window-c"></a>Fenêtre Définition de code (C++)

La fenêtre **Définition de code** affiche la définition d’un type C++ ou membre sélectionné dans le projet actif. Le type ou le membre peut être sélectionné dans l'éditeur de code ou dans une fenêtre d'affichage de code.

Cette fenêtre est en lecture seule mais vous pouvez y définir des points d'arrêt ou des signets. Pour modifier la définition affichée, choisissez **Modifier la définition** dans le menu contextuel. Cela ouvre le fichier source dans l'éditeur de code et place le point d'insertion sur la ligne où la définition commence.

> [!NOTE]
> À compter de Visual Studio 2015, la fenêtre **définition de code** ne peut être utilisée qu’avec du code C++.

### <a name="code-definition-shortcut-menu"></a>Menu contextuel de la fenêtre Définition de code

Le menu contextuel (ou clic droit) dans la fenêtre **définition de code** peut contenir les commandes suivantes :

|Nom|Description|
|-|-|
|**Actions rapides et refactorisations**||
|**Renommer**||
|**Générer le graphique des fichiers include**||
|**Aperçu de définition**||
|**Atteindre la définition**|Recherche la définition (ou les définitions, pour des classes partielles) et l’affiche dans une fenêtre **Résultats de la recherche**.|
|**Atteindre la déclaration**||
|**Rechercher toutes les références**|Recherche les références au type ou au membre dans la solution.|
|**Afficher la hiérarchie d’appels**|Affiche la méthode dans la fenêtre **Hiérarchie d’appels**.|
|**Afficher ou masquer l'en-tête / le fichier de code**||
|**Exécuter les tests**|S'il existe des tests unitaires dans le projet, exécute les tests pour le code sélectionné.|
|**Déboguer les tests**||
|**Point d’arrêt**|Insère un point d'arrêt (ou un point de trace).|
|**Exécuter jusqu’au curseur**|Exécute le programme en mode débogage jusqu'à l'emplacement du curseur.|
|**Extrait**||
|**Cut**, **Copy**, **Paste**||
|**Annotation**||
|**mode Plan**|Commandes de mode Plan standard.|
|**Relancer**||
|**Modifier la définition**|Déplace le point d'insertion vers la définition dans la fenêtre de code.|
|**Choisir l’encodage**|Ouvre la fenêtre **Encodage** afin que vous puissiez définir un encodage pour le fichier.|

## <a name="document-outline-window"></a>Fenêtre Structure du document

Vous pouvez utiliser la fenêtre **Structure du document** conjointement aux vues de concepteurs comme le concepteur pour une page XAML ou un concepteur Windows Form, ou avec des pages HTML. Cette fenêtre affiche les éléments dans une arborescence, afin que vous puissiez consulter la structure logique du formulaire ou de la page et rechercher des contrôles incorporés en profondeur ou masqués.

## <a name="see-also"></a>Voir aussi

- [Icônes Affichage de classes et Explorateur d’objets](../ide/class-view-and-object-browser-icons.md)
