---
title: Création et configuration de membres de type (Concepteur de classes)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ba5c26ece60c6689509054b733109ee11799ccd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55010075"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Créer et configurer des membres de type dans le Concepteur de classes

Vous pouvez ajouter ces membres aux types dans un diagramme de classes et configurer ces membres dans la fenêtre **Détails de classe** :

|**Type**|**Membres qu’il peut contenir**|
|--------------| - |
|Classe|méthode, propriété (pour C# et Visual Basic), champ, événement (pour C# et Visual Basic), constructeur (méthode), destructeur (méthode), constante|
|Enum|member|
|Interface|méthode, propriété, événement (pour C# et Visual Basic)|
|Classe abstraite|méthode, propriété (pour C# et Visual Basic), champ, événement (pour C# et Visual Basic), constructeur (méthode), destructeur (méthode), constante|
|Structure (Struct en C#)|méthode, propriété (pour C# et Visual Basic) champ, événement (pour C# et Visual Basic), constructeur (méthode), constante|
|délégué|parameter|
|Module (VB uniquement)|méthode, propriété, champ, événement, constructeur, constante|

> [!NOTE]
> Lorsque les accesseurs get et set d’une propriété ne requièrent aucune logique supplémentaire, simplifiez la déclaration de la propriété en utilisant des propriétés implémentées automatiquement (C# uniquement). Pour afficher la signature complète, dans le menu **Diagramme de classes**, choisissez **Modifier le format des membres** > **Afficher la signature complète**. Pour plus d’informations sur les propriétés implémentées automatiquement, consultez [Propriétés implémentées automatiquement](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu de support|
|----------| - |
|**Bien démarrer :** avant de créer et de configurer des membres de type, vous devez ouvrir la fenêtre **Détails de classe**.|- [Ouvrir la fenêtre Détails de classe](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Notes d’utilisation de la fenêtre Détails de classe](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Affichage d’informations en lecture seule](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Créer et modifier des membres de type :** vous pouvez créer des membres, en modifier et ajouter des paramètres à une méthode avec la fenêtre **Détails de classe**.|- [Créer des membres](creating-and-configuring-type-members.md#create-members)<br />- [Modifier des membres de type](creating-and-configuring-type-members.md#modify-type-members)<br />- [Ajouter des paramètres aux méthodes](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Ouvrir la fenêtre Détails de classe

Par défaut, la fenêtre **Détails de classe** s’affiche automatiquement quand vous ouvrez un nouveau diagramme de classes. Voir [Guide pratique pour ajouter des diagrammes de classes à des projets](how-to-add-class-diagrams-to-projects.md). Vous pouvez aussi ouvrir la fenêtre **Détails de classe** des manières suivantes :

- Cliquez avec le bouton droit sur une classe du diagramme pour afficher un menu contextuel, puis sélectionnez **Détails de classe**.

- Sélectionnez **Affichage** > **Autres fenêtres** > **Détails de classe** dans la barre de menus.

## <a name="create-members"></a>Créer des membres

Vous pouvez créer un membre à l'aide de l'un des outils suivants :

- **Concepteur de classes**

- Barre d’outils de la fenêtre **Détails de classe**

- Fenêtre **Détails de classe**

> [!NOTE]
> Vous pouvez aussi créer des constructeurs et des destructeurs à l'aide des procédures de cette section. N’oubliez pas que les constructeurs et les destructeurs constituent des genres particuliers de méthodes et que, comme tels, ils apparaissent dans le compartiment **Méthodes** des formes du diagramme de classes et dans la section **Méthodes** de la grille de fenêtre **Détails de classe**.

> [!NOTE]
> La seule entité que vous pouvez ajouter à un délégué est un paramètre. Notez que la procédure intitulée « Pour créer un membre à l’aide de la barre d’outils de la fenêtre **Détails de classe** » n’est pas valide pour cette action.

### <a name="create-a-member-using-class-designer"></a>Créer un membre à l’aide du Concepteur de classes

1.  Cliquez avec le bouton droit sur le type auquel vous souhaitez ajouter un membre, pointez sur **Ajouter**, puis choisissez le type de membre à ajouter.

     Une nouvelle signature de membre est créée et ajoutée au type. Le nom attribué par défaut peut être modifié dans le **Concepteur de classes**, la fenêtre **Détails de classe** ou la fenêtre **Propriétés**.

2.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le membre, comme son type.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Créer un membre à l’aide de la barre d’outils de la fenêtre Détails de classe

1.  Sur la surface du diagramme, sélectionnez le type auquel vous souhaitez ajouter un membre.

     Le type obtient le focus et son contenu est affiché dans la fenêtre **Détails de classe**.

2.  Dans la barre d’outils de la fenêtre **Détails de classe**, cliquez sur l’icône supérieure et sélectionnez **Nouveau \<membre>** dans la liste déroulante.

     Le curseur se déplace sur le champ **Nom** d’une ligne pour le genre de membre que vous souhaitez ajouter. Par exemple, si vous avez cliqué sur **Nouvelle propriété**, le curseur se déplace sur une nouvelle ligne dans la section **Propriétés** de la fenêtre **Détails de classe**.

3.  Tapez le nom du membre que vous voulez créer et appuyez sur Entrée (ou déplacez le focus en appuyant sur la touche TAB).

     Une nouvelle signature de membre est créée et ajoutée au type. Le membre, qui existe maintenant dans le code, est affiché dans le **Concepteur de classes**, la fenêtre **Détails de classe** et la fenêtre Propriétés.

4.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le membre, comme son type.

### <a name="create-a-member-using-the-class-details-window"></a>Créer un membre à l’aide de la fenêtre Détails de classe

1.  Sur la surface du diagramme, sélectionnez le type auquel vous souhaitez ajouter un membre.

     Le type obtient le focus et son contenu est affiché dans la fenêtre **Détails de classe**.

2.  Dans la fenêtre **Détails de classe**, dans la section contenant le genre de membre que vous souhaitez ajouter, cliquez sur **\<ajouter un membre>**. Par exemple, pour ajouter un champ, cliquez sur **\<ajouter un champ>**.

3.  Tapez le nom du membre que vous voulez créer et appuyez sur Entrée.

     Une nouvelle signature de membre est créée et ajoutée au type. Le membre existe maintenant dans le code. Il est affiché dans le **Concepteur de classes**, la fenêtre **Détails de classe** et la fenêtre Propriétés.

4.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le membre, comme son type.

     **Remarque :** vous pouvez aussi utiliser les raccourcis clavier pour créer des membres. Pour plus d’informations, consultez [Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Modifier des membres de type

Le Concepteur de classes permet de modifier les membres de types affichés sur le diagramme. Vous pouvez modifier les membres de n'importe quel type affiché sur un diagramme de classes, à condition que ce type ne soit pas en lecture seule. Pour modifier des membres de type, utilisez la modification sur place sur l’aire de conception, la fenêtre Propriétés et la fenêtre **Détails de classe**.

Tous les membres affichés dans la fenêtre **Détails de classe** représentent les membres des types figurant dans le diagramme de classes. Il existe quatre types de membres : les méthodes, les propriétés, les champs et les événements.

Toutes les lignes membres apparaissent sous les en-têtes qui regroupent les membres par genre. Par exemple, toutes les propriétés apparaissent sous l’en-tête **Propriétés**, lequel peut être réduit ou développé, comme tout nœud de la grille.

Chaque ligne membre affiche les éléments suivants :

- **Icône Membre**

     Chaque genre de membre est représenté par sa propre icône. Pointez la souris sur l’icône de membre pour afficher la signature du membre. Cliquez sur l'icône de membre ou sur l'espace blanc à gauche de l'icône de membre pour sélectionner la ligne.

- **Nom du membre**

     La colonne **Nom** d’une ligne membre affiche le nom du membre. Ce nom est également affiché dans la propriété **Nom** de la fenêtre Propriétés. Utilisez cette cellule pour modifier le nom d'un membre qui dispose d'autorisations en lecture-écriture.

     Si la colonne **Nom** est trop étroite pour afficher le nom entier, le fait de pointer la souris sur le nom de membre permet d’afficher l’intégralité du nom.

- **Type de membre**

     La cellule **Type de membre** utilise la technologie IntelliSense, qui vous permet de faire une sélection au sein de la liste de tous les types disponibles du projet en cours ou des projets référencés.

- **Modificateur de membre**

     Modifiez le modificateur de visibilité d’un membre en `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`) ou `Default`.

- **\<ajouter un membre>**

     La dernière ligne de la fenêtre **Détails de classe** contient le texte **\<ajouter un membre>** dans la cellule **Nom**. Si vous cliquez sur cette cellule, vous pouvez créer un membre. Pour plus d’informations, consultez [Créer des membres](creating-and-configuring-type-members.md#create-members).

- **Propriétés du membre dans la fenêtre Propriétés**

     La fenêtre **Détails de classe** affiche un sous-ensemble des propriétés du membre affichées dans la fenêtre Propriétés. La modification d'une propriété dans un emplacement met à jour la valeur de la propriété de façon globale. Cela inclut l'affichage de sa valeur dans l'autre emplacement.

- **Résumé**

     La cellule **Résumé** contient un résumé des informations sur le membre. Cliquez sur les points de suspension dans la cellule **Résumé** pour afficher ou modifier les informations sur le **Résumé**, le **Type de retour** et les **Notes** du membre.

- **Masquer**

     Quand la case **Masquer** est cochée, le membre n’est pas affiché dans le type.

### <a name="to-modify-a-type-member"></a>Pour modifier un membre de type

1.  À l'aide du Concepteur de classes, sélectionnez un type.

2.  Si la fenêtre **Détails de classe** n’est pas affichée, cliquez sur le bouton de la fenêtre **Détails de classe** dans la barre d’outils du Concepteur de classes.

3.  Modifiez les valeurs des champs de la grille de la fenêtre **Détails de classe**. Après chaque modification, appuyez sur ENTRÉE ou éloignez le focus du champ modifié, par exemple en appuyant sur la touche TAB. Les modifications sont immédiatement répercutées dans le code.

    > [!NOTE]
    > Si vous souhaitez modifier uniquement le nom d'un membre, vous pouvez le faire à l'aide de la modification sur place.

## <a name="add-parameters-to-methods"></a>Ajouter des paramètres aux méthodes

Ajoutez des paramètres aux méthodes à l’aide de la fenêtre **Détails de classe**. Les paramètres peuvent être configurés pour être obligatoires ou optionnels. La valeur de la propriété **Valeur par défaut facultative** d’un paramètre demande au concepteur de générer le code en tant que paramètre optionnel.

Les lignes de paramètres contiennent les éléments suivants :

- **Name**

     La colonne **Nom** d’une ligne de paramètre affiche le nom du paramètre. Ce nom est également affiché dans la propriété **Nom** de la fenêtre Propriétés. Vous pouvez utiliser cette cellule pour modifier le nom d'un paramètre ayant les autorisations en lecture-écriture.

     Le fait de pointer sur le nom du paramètre affiche celui-ci si la colonne **Nom** est trop étroite pour afficher la totalité du nom.

- **Type**

     La cellule **Type de paramètre** utilise la technologie IntelliSense, qui permet de choisir dans la liste de tous les types disponibles du projet en cours ou des projets référencés.

- **Modificateur**

     La cellule **Modificateur** d’une ligne de paramètre accepte le nouveau modificateur du paramètre et l’affiche. Pour entrer un nouveau modificateur de paramètre, utilisez la zone de liste déroulante pour faire votre choix : **Aucun**, **ref**, **out** ou **params** dans C#, et **ByVal**, **ByRef** ou **ParamArray** dans Visual Basic.

- **Résumé**

     La cellule **Résumé** d’une ligne de paramètre permet d’entrer des commentaires de code qui s’affichent dans IntelliSense lors de la saisie du paramètre dans l’éditeur de code.

- **\<ajouter un paramètre>**

     La dernière ligne de paramètre d’un membre contient le texte **<add parameter>** dans la cellule**Nom**. Cliquez sur cette cellule pour créer un nouveau paramètre. Pour plus d’informations, consultez [Pour ajouter un paramètre à une méthode](creating-and-configuring-type-members.md#add-parameters-to-methods).

La fenêtre **Propriétés** présente les mêmes propriétés de paramètres que la fenêtre **Détails de classe** : **Nom**, **Type**, **Modificateur**, **Résumé**, ainsi que la propriété **Valeur par défaut facultative**. La modification d'une propriété dans un emplacement met à jour la valeur de la propriété de manière globale, y compris l'affichage de sa valeur dans l'autre emplacement.

> [!NOTE]
> Pour ajouter un paramètre à un délégué, consultez [Créer des membres](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Bien qu'un destructeur soit une méthode, il ne peut pas avoir de paramètres.

### <a name="to-add-a-parameter-to-a-method"></a>Pour ajouter un paramètre à une méthode

1.  Sur la surface du diagramme, cliquez sur le type qui contient la méthode à laquelle vous souhaitez ajouter un paramètre.

     Le type obtient le focus et son contenu est affiché dans la fenêtre **Détails de classe**.

2.  Dans la fenêtre **Détails de classe**, développez la ligne de la méthode à laquelle vous souhaitez ajouter un paramètre.

     Une ligne de paramètre mise en retrait s’affiche ; elle contient uniquement une paire de parenthèses et les mots **\<ajouter un paramètre>**.

3.  Cliquez sur **\<ajouter un paramètre>**, tapez le nom du nouveau paramètre et appuyez sur **Entrée**.

     Le nouveau paramètre est ajouté à la méthode et à son code. Il apparaît dans la fenêtre **Détails de classe** et dans la fenêtre Propriétés.

4.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le paramètre, comme son type.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Pour ajouter un paramètre optionnel à une méthode

1.  Sur la surface du diagramme, cliquez sur le type qui contient la méthode à laquelle vous souhaitez ajouter un paramètre optionnel.

     Le type obtient le focus et son contenu est affiché dans la fenêtre **Détails de classe**.

2.  Dans la fenêtre **Détails de classe**, développez la ligne de la méthode à laquelle vous souhaitez ajouter un paramètre optionnel.

     Une ligne de paramètre mise en retrait s’affiche ; elle contient uniquement une paire de parenthèses et les mots **\<ajouter un paramètre>**.

3.  Cliquez sur **\<ajouter un paramètre>**, tapez le nom du nouveau paramètre et appuyez sur **Entrée**.

     Le nouveau paramètre est ajouté à la méthode et à son code. Il apparaît dans la fenêtre **Détails de classe** et dans la fenêtre Propriétés.

4.  Dans la fenêtre Propriétés, tapez une valeur pour la propriété **Valeur par défaut facultative**. La définition de la propriété Valeur par défaut facultative d'un paramètre rend ce paramètre optionnel.

    > [!NOTE]
    > Les paramètres optionnels doivent être les derniers paramètres dans la liste de paramètres.

## <a name="class-details-usage-notes"></a>Notes d’utilisation de la fenêtre Détails de classe

Notez les conseils suivants pour utiliser la fenêtre **Détails de classe**.

### <a name="editable-and-non-editable-cells"></a>Cellules modifiables et cellules non modifiables

Toutes les cellules de la fenêtre **Détails de classe** sont modifiables, à quelques exceptions près :

- Le type est en lecture seule, quand, par exemple, il réside dans un assembly référencé. Quand vous sélectionnez la forme dans le Concepteur de classes, la fenêtre **Détails de classe** affiche ses détails en lecture seule.

- Pour les indexeurs, le nom est en lecture seule et le reste (type, modificateur, résumé) est modifiable.

- Tous les génériques ont des paramètres en lecture seule dans la fenêtre **Détails de classe**. Pour modifier un paramètre générique, modifiez son code source.

- Le nom du paramètre de type qui est défini sur un type générique est en lecture seule.

- Quand le code d’un type est rompu (non analysable), la fenêtre **Détails de classe** affiche le contenu du type en lecture seule.

### <a name="the-class-details-window-and-source-code"></a>Fenêtre Détails de classe et code source

- Vous pouvez consulter le code source en cliquant avec le bouton droit sur une forme de la fenêtre **Détails de classe** (ou du Concepteur de classes), puis en cliquant sur Afficher le code. Le fichier correspondant s'ouvre et le code source défile jusqu'à l'élément sélectionné.

- Le changement du code source est immédiatement répercuté dans l’affichage des informations de signature dans le Concepteur de classes ou dans la fenêtre **Détails de classe**. Si la fenêtre **Détails de classe** est fermée à ce moment-là, les nouvelles informations ne seront visibles qu’à la prochaine ouverture.

- Quand le code d’un type est rompu (non analysable), la fenêtre **Détails de classe** affiche le contenu du type en lecture seule.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Utilisation du Presse-papiers dans la fenêtre Détails de classe

Vous pouvez copier ou couper des champs ou des lignes dans la fenêtre **Détails de classe** et les coller dans un autre type. Vous ne pouvez couper une ligne que si elle n'est pas en lecture seule. Quand vous collez la ligne, la fenêtre **Détails de classe** assigne un nouveau nom (dérivé du nom de la ligne copiée) pour éviter tout conflit.

## <a name="display-of-read-only-information"></a>Affichage d’informations en lecture seule

Le Concepteur de classes et la fenêtre **Détails de classe peuvent** afficher les types (et les membres de types) des éléments suivants :

- projet contenant un diagramme de classes

- projet référencé d'un projet contenant un diagramme de classes

- assembly référencé d'un projet contenant un diagramme de classes

Dans les deux derniers cas, l'entité référencée (un type ou un membre) est en lecture seule dans le diagramme de classes qui la représente.

Tout ou partie (certains fichiers, par exemple) d'un projet peut être en lecture seule. Les cas les plus communs où un projet ou l'un de ses fichiers est en lecture seule se produisent quand le projet ou le fichier est sous contrôle du code source (et n'a pas été extrait), qu'il existe dans un assembly externe ou que le système d'exploitation considère les fichiers comme étant en lecture seule.

**Contrôle du code source**

Étant donné qu’un diagramme de classes est enregistré comme fichier dans un projet, vous devez extraire le projet pour enregistrer tous les changements apportés dans le Concepteur de classes ou dans la fenêtre **Détails de classe**.

**Projets en lecture seule**

Le projet peut être en lecture seule pour une autre raison que le contrôle du code source. La fermeture du projet affiche une boîte de dialogue qui demande si vous souhaitez remplacer le fichier projet, ignorer les modifications (aucun enregistrement) ou annuler l’opération de fermeture. Si vous faites le choix du remplacement, les fichiers projet sont remplacés et rendus accessibles en lecture-écriture. Le nouveau fichier du diagramme de classes est ajouté.

**Types en lecture seule**

Si vous essayez d’enregistrer un projet contenant un type dont le fichier de code source est en lecture seule, la boîte de dialogue **Enregistrement d’un fichier accessible en lecture seule** qui apparaît vous donne le choix entre enregistrer le fichier sous un nouveau nom (ou à un nouvel emplacement) ou remplacer le fichier en lecture seule. Si vous remplacez le fichier, la nouvelle copie n'est plus en lecture seule.

Si un fichier de code contient une erreur de syntaxe, les formes dédiées à l'affichage du code de ce fichier restent en lecture seule tant que l'erreur de syntaxe n'est pas résolue. Les formes affichent alors le texte en rouge et une icône de couleur rouge, accompagnée d'une info-bulle dont le texte est le suivant : « Le fichier de code source contient une erreur d'analyse. »

Un type référencé (comme un type .NET Framework), qui existe sous un autre nœud de projet ou sous un nœud d'assembly référencé, est signalé sur l'aire de conception du Concepteur de classes comme étant en lecture seule. Un type local, qui existe dans le projet que vous a ouvert, est en lecture-écriture, et sa forme sur l'aire de conception du Concepteur de classes est indiquée comme telle.

Les indexeurs sont en lecture-écriture dans le code et dans la fenêtre **Détails de classe**, mais le nom d’indexeur est en lecture seule.

Vous ne pouvez pas modifier de méthodes partielles à l’aide du Concepteur de classes ou de la fenêtre **Détails de classe**. Pour réaliser cette opération, vous devez utiliser l’éditeur de code.

Vous ne pouvez pas modifier de code C++ natif à l’aide du Concepteur de classes ou de la fenêtre **Détails de Classe**. Pour réaliser cette opération, vous devez utiliser l’éditeur de code.

## <a name="see-also"></a>Voir aussi

- [Affichage des types et des relations](designing-and-viewing-classes-and-types.md)
- [Refactorisation des classes et des types](refactoring-classes-and-types.md)