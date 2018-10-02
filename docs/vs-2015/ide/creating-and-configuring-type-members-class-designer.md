---
title: Création et configuration de membres de type (Concepteur de classes) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2e93f9cd0e1fb35a1698b0795972abc09527c038
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47516668"
---
# <a name="creating-and-configuring-type-members-class-designer"></a>Création et configuration de membres de type (Concepteur de classes)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez ajouter ces membres aux types dans un diagramme de classes et configurer ces membres dans la fenêtre **Détails de classe** :  
  
|**Type**|**Membres qu’il peut contenir**|  
|--------------|--------------------------------|  
|Classe|méthode, propriété (pour C# et Visual Basic), champ, événement (pour C# et Visual Basic), constructeur (méthode), destructeur (méthode), constante|  
|Enum|member|  
|Interface|méthode, propriété, événement (pour C# et Visual Basic)|  
|Classe abstraite|méthode, propriété (pour C# et Visual Basic), champ, événement (pour C# et Visual Basic), constructeur (méthode), destructeur (méthode), constante|  
|Structure (Struct en C#)|méthode, propriété (pour C# et Visual Basic) champ, événement (pour C# et Visual Basic), constructeur (méthode), constante|  
|délégué|Paramètre|  
|Module (VB uniquement)|méthode, propriété, champ, événement, constructeur, constante|  
  
> [!NOTE]
>  Lorsque les accesseurs get et set d’une propriété ne requièrent aucune logique supplémentaire, simplifiez la déclaration de la propriété en utilisant des propriétés implémentées automatiquement (C# uniquement). Pour afficher la signature complète, dans le menu **Diagramme de classes**, choisissez **Modifier le format des membres**, **Afficher la signature complète**. Pour plus d’informations sur les propriétés implémentées automatiquement, consultez [Propriétés implémentées automatiquement](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7).  
  
## <a name="common-tasks"></a>Tâches courantes  
  
|Tâche|Contenu de support|  
|----------|------------------------|  
|**Prise en main** : avant de créer et de configurer des membres de type, vous devez ouvrir la fenêtre Détails de classe.|-   [Ouverture de la fenêtre Détails de classe](../ide/creating-and-configuring-type-members-class-designer.md#OpenClassDetails)<br />-   [Notes d’utilisation de la fenêtre Détails de classe](../ide/creating-and-configuring-type-members-class-designer.md#ClassDetailsUsageNotes)<br />-   [Affichage d’informations en lecture seule](../ide/creating-and-configuring-type-members-class-designer.md#ReadOnlyInfo)<br />-   [Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe (Concepteur de classes)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md)|  
|**Créer et modifier les membres de type** : vous pouvez créer d’autres membres, modifier des membres existants et ajouter des paramètres à une méthode à l’aide de la fenêtre Détails de classe.|-   [Création de membres](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers)<br />-   [Modification des membres de type](../ide/creating-and-configuring-type-members-class-designer.md#ModifyTypeMembers)<br />-   [Ajout de paramètres aux méthodes](../ide/creating-and-configuring-type-members-class-designer.md#AddMethodParams)|  
  
##  <a name="OpenClassDetails"></a> Ouverture de la fenêtre Détails de classe  
 Par défaut, la fenêtre Détails de classe s’affiche automatiquement quand vous ouvrez un nouveau diagramme de classes (consultez [Guide pratique pour ajouter des diagrammes de classes aux projets (Concepteur de classes)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)). Vous pouvez aussi ouvrir explicitement la fenêtre Détails de classe, comme indiqué ci-après.  
  
#### <a name="to-open-the-class-details-window"></a>Pour ouvrir la fenêtre Détails de classe  
  
1.  Cliquez avec le bouton droit sur une classe du diagramme pour afficher un menu contextuel.  
  
2.  Dans le menu contextuel, cliquez sur **Fenêtre Détails de classe**.  
  
 - ou -  
  
-   Pointez sur **Autres fenêtres** dans le menu Affichage, puis cliquez sur **Détails de classe**.  
  
##  <a name="CreateMembers"></a> Création de membres  
 Vous pouvez créer un membre à l'aide de l'un des outils suivants :  
  
-   Concepteur de classes  
  
-   Barre d'outils de la fenêtre Détails de classe  
  
-   Fenêtre Détails de classe  
  
> [!NOTE]
>  Vous pouvez aussi créer des constructeurs et des destructeurs à l'aide des procédures de cette section. N’oubliez pas que les constructeurs et les destructeurs constituent des genres particuliers de méthodes et que, comme tels, ils apparaissent dans le compartiment **Méthodes** des formes du diagramme de classes et dans la section **Méthodes** de la grille de fenêtre Détails de classe.  
  
> [!NOTE]
>  La seule entité que vous pouvez ajouter à un délégué est un paramètre. Notez que la procédure intitulée « Pour créer un membre à l'aide de la barre d'outils de la fenêtre Détails de classe » n'est pas valide pour cette action.  
  
#### <a name="to-create-a-member-using-class-designer"></a>Pour créer un membre à l'aide du Concepteur de classes  
  
1.  Cliquez avec le bouton droit sur le type auquel vous souhaitez ajouter un membre, pointez sur **Ajouter**, puis choisissez le type de membre à ajouter.  
  
     Une nouvelle signature de membre est créée et ajoutée au type. Le nom attribué par défaut peut être modifié dans le **Concepteur de classes**, la fenêtre **Détails de classe** ou la fenêtre **Propriétés**.  
  
2.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le membre, comme son type.  
  
#### <a name="to-create-a-member-using-the-class-details-window-toolbar"></a>Pour créer un membre à l'aide de la barre d'outils de la fenêtre Détails de classe  
  
1.  Sur la surface du diagramme, sélectionnez le type auquel vous souhaitez ajouter un membre.  
  
     Le type obtient le focus et son contenu est affiché dans la fenêtre Détails de classe.  
  
2.  Dans la barre d’outils de la fenêtre Détails de classe, cliquez sur l’icône supérieure et sélectionnez **Nouveau \<membre>** dans la liste déroulante.  
  
     Le curseur se déplace sur le champ **Nom** d’une ligne pour le genre de membre que vous souhaitez ajouter. Par exemple, si vous avez cliqué sur **Nouvelle propriété**, le curseur se déplace sur une nouvelle ligne dans la section **Propriétés** de la fenêtre Détails de classe.  
  
3.  Tapez le nom du membre que vous voulez créer et appuyez sur Entrée (ou déplacez le focus en appuyant sur la touche TAB).  
  
     Une nouvelle signature de membre est créée et ajoutée au type. Le membre existe maintenant dans le code ; il est affiché dans le **Concepteur de classes**, la fenêtre Détails de classe et la fenêtre Propriétés.  
  
4.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le membre, comme son type.  
  
#### <a name="to-create-a-member-using-the-class-details-window"></a>Pour créer un membre à l'aide de la fenêtre Détails de classe  
  
1.  Sur la surface du diagramme, sélectionnez le type auquel vous souhaitez ajouter un membre.  
  
     Le type obtient le focus et son contenu est affiché dans la fenêtre Détails de classe.  
  
2.  Dans la fenêtre Détails de classe, dans la section contenant le genre de membre que vous souhaitez ajouter, cliquez sur **\<ajouter un membre>**. Par exemple, pour ajouter un champ, cliquez sur **\<ajouter un champ>**.  
  
3.  Tapez le nom du membre que vous voulez créer et appuyez sur Entrée.  
  
     Une nouvelle signature de membre est créée et ajoutée au type. Le membre existe maintenant dans le code ; il est affiché dans le **Concepteur de classes**, la fenêtre Détails de classe et la fenêtre Propriétés.  
  
4.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le membre, comme son type.  
  
     **Remarque :** Vous pouvez aussi utiliser des raccourcis clavier pour créer les membres. Pour plus d’informations, consultez [Raccourcis clavier et souris dans le diagramme de classes et dans la fenêtre Détails de classe (Concepteur de classes)](../ide/keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window-class-designer.md).  
  
##  <a name="ModifyTypeMembers"></a> Modification des membres de type  
 Le Concepteur de classes permet de modifier les membres de types affichés sur le diagramme. Vous pouvez modifier les membres de n'importe quel type affiché sur un diagramme de classes, à condition que ce type ne soit pas en lecture seule. Consultez [Affichage d’informations en lecture seule (Concepteur de classes)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a). Pour modifier des membres de type, utilisez la modification sur place sur l'aire de conception, la fenêtre Propriétés et la fenêtre Détails de classe.  
  
 Tous les membres affichés dans la fenêtre Détails de classe représentent les membres des types figurant dans le diagramme de classes. Il existe quatre types de membres : les méthodes, les propriétés, les champs et les événements.  
  
 Toutes les lignes membres apparaissent sous les en-têtes qui regroupent les membres par genre. Par exemple, toutes les propriétés apparaissent sous l’en-tête **Propriétés**, lequel peut être réduit ou développé, comme tout nœud de la grille.  
  
 Chaque ligne membre affiche les éléments suivants :  
  
-   **Icône Membre**  
  
     Chaque genre de membre est représenté par sa propre icône. Pointez la souris sur l'icône de membre pour afficher la signature du membre. Cliquez sur l'icône de membre ou sur l'espace blanc à gauche de l'icône de membre pour sélectionner la ligne.  
  
-   **Nom du membre**  
  
     La colonne **Nom** d’une ligne membre affiche le nom du membre. Ce nom est également affiché dans la propriété **Nom** de la fenêtre Propriétés. Utilisez cette cellule pour modifier le nom d'un membre qui dispose d'autorisations en lecture-écriture.  
  
     Si la colonne **Nom** est trop étroite pour afficher le nom entier, le fait de pointer la souris sur le nom de membre permet d’afficher l’intégralité du nom.  
  
-   **Type de membre**  
  
     La cellule **Type de membre** utilise la technologie IntelliSense, qui vous permet de faire une sélection au sein de la liste de tous les types disponibles du projet en cours ou des projets référencés.  
  
-   **Modificateur de membre**  
  
     Modifiez le modificateur de visibilité d’un membre en `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected``Friend` (`protected``internal`) ou `Default`.  
  
-   **\<ajouter un membre>**  
  
     La dernière ligne de la fenêtre Détails de classe contient le texte **\<ajouter un membre>** dans la cellule **Nom**. Si vous cliquez sur cette cellule, vous pouvez créer un membre. Pour plus d’informations, consultez [Création de membres](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
-   **Propriétés du membre dans la fenêtre Propriétés**  
  
     La fenêtre Détails de classe affiche un sous-ensemble des propriétés du membre affichées dans la fenêtre Propriétés. La modification d'une propriété dans un emplacement met à jour la valeur de la propriété de façon globale. Cela inclut l'affichage de sa valeur dans l'autre emplacement.  
  
-   **Résumé**  
  
     La cellule **Résumé** contient un résumé des informations sur le membre. Cliquez sur les points de suspension dans la cellule **Résumé** pour afficher ou modifier les informations sur le **Résumé**, le **Type de retour** et les **Notes** du membre.  
  
-   **Masquer**  
  
     Quand la case **Masquer** est cochée, le membre n’est pas affiché dans le type.  
  
#### <a name="to-modify-a-type-member"></a>Pour modifier un membre de type  
  
1.  À l'aide du Concepteur de classes, sélectionnez un type.  
  
2.  Si la fenêtre Détails de classe n’est pas affichée, cliquez sur le bouton **Fenêtre Détails de classe** dans la barre d’outils du Concepteur de classes.  
  
3.  Modifiez les valeurs des champs de la grille de la fenêtre Détails de classe. Après chaque modification, appuyez sur ENTRÉE ou éloignez le focus du champ modifié, par exemple en appuyant sur la touche TAB. Les modifications sont immédiatement répercutées dans le code.  
  
    > [!NOTE]
    >  Si vous souhaitez modifier uniquement le nom d'un membre, vous pouvez le faire à l'aide de la modification sur place.  
  
##  <a name="AddMethodParams"></a> Ajout de paramètres aux méthodes  
 Ajoutez des paramètres aux méthodes à l'aide de la fenêtre Détails de classe. Les paramètres peuvent être configurés pour être obligatoires ou optionnels. La valeur de la propriété **Valeur par défaut facultative** d’un paramètre demande au concepteur de générer le code en tant que paramètre optionnel.  
  
 Les lignes de paramètres contiennent les éléments suivants :  
  
-   **Name**  
  
     La colonne **Nom** d’une ligne de paramètre affiche le nom du paramètre. Ce nom est également affiché dans la propriété **Nom** de la fenêtre Propriétés. Vous pouvez utiliser cette cellule pour modifier le nom d'un paramètre ayant les autorisations en lecture-écriture.  
  
     Le fait de pointer sur le nom du paramètre affiche celui-ci si la colonne **Nom** est trop étroite pour afficher la totalité du nom.  
  
-   **Type**  
  
     La cellule **Type de paramètre** utilise la technologie Intellisense, qui permet de choisir au sein de la liste de tous les types disponibles du projet en cours ou des projets référencés.  
  
-   **Modificateur**  
  
     La cellule **Modificateur** d’une ligne de paramètre accepte le nouveau modificateur du paramètre et l’affiche. Pour entrer un nouveau modificateur de paramètre, utilisez la zone de liste déroulante pour faire votre choix : **Aucun**, **ref**, **out** ou **params** dans C#, et **ByVal**, **ByRef** ou **ParamArray** dans Visual Basic.  
  
-   **Résumé**  
  
     La cellule **Résumé** d’une ligne de paramètre permet d’entrer des commentaires de code qui s’affichent dans IntelliSense lors de la saisie du paramètre dans l’éditeur de code.  
  
-   **\<ajouter un paramètre>**  
  
     La dernière ligne de paramètre d’un membre contient le texte **<add parameter>** dans la cellule**Nom**. Cliquez sur cette cellule pour créer un nouveau paramètre. Pour plus d’informations, consultez [Pour ajouter un paramètre à une méthode](../ide/creating-and-configuring-type-members-class-designer.md#HowToAddParameterToMethod).  
  
 **Propriétés des paramètres dans la fenêtre Propriétés**  
  
 La fenêtre Propriétés affiche les mêmes propriétés de paramètre que celles affichées dans la fenêtre Détails de classe : **Nom**, **Type**, **Modificateur**, **Résumé**, ainsi que la propriété **Valeur par défaut facultative**. La modification d'une propriété dans un emplacement met à jour la valeur de la propriété de manière globale, y compris l'affichage de sa valeur dans l'autre emplacement.  
  
> [!NOTE]
>  Pour ajouter un paramètre à un délégué, consultez [Création de membres](../ide/creating-and-configuring-type-members-class-designer.md#CreateMembers).  
  
> [!NOTE]
>  Bien qu'un destructeur soit une méthode, il ne peut pas avoir de paramètres.  
  
###  <a name="HowToAddParameterToMethod"></a> Pour ajouter un paramètre à une méthode  
  
1.  Sur la surface du diagramme, cliquez sur le type qui contient la méthode à laquelle vous souhaitez ajouter un paramètre.  
  
     Le type obtient le focus et son contenu est affiché dans la fenêtre Détails de classe.  
  
2.  Dans la fenêtre Détails de classe, développez la ligne de la méthode à laquelle vous souhaitez ajouter un paramètre.  
  
     Une ligne de paramètre mise en retrait s’affiche ; elle contient uniquement une paire de parenthèses et les mots **\<ajouter un paramètre>**.  
  
3.  Cliquez sur **\<ajouter un paramètre>**, tapez le nom du nouveau paramètre et appuyez sur **Entrée**.  
  
     Le nouveau paramètre est ajouté à la méthode et à son code. Il apparaît dans la fenêtre Détails de classe et dans la fenêtre Propriétés.  
  
4.  Vous pouvez, à titre facultatif, spécifier d'autres détails sur le paramètre, comme son type.  
  
### <a name="to-add-an-optional-parameter-to-a-method"></a>Pour ajouter un paramètre optionnel à une méthode  
  
1.  Sur la surface du diagramme, cliquez sur le type qui contient la méthode à laquelle vous souhaitez ajouter un paramètre optionnel.  
  
     Le type obtient le focus et son contenu est affiché dans la fenêtre Détails de classe.  
  
2.  Dans la fenêtre Détails de classe, développez la ligne de la méthode à laquelle vous souhaitez ajouter un paramètre optionnel.  
  
     Une ligne de paramètre mise en retrait s’affiche ; elle contient uniquement une paire de parenthèses et les mots **\<ajouter un paramètre>**.  
  
3.  Cliquez sur **\<ajouter un paramètre>**, tapez le nom du nouveau paramètre et appuyez sur **Entrée**.  
  
     Le nouveau paramètre est ajouté à la méthode et à son code. Il apparaît dans la fenêtre Détails de classe et dans la fenêtre Propriétés.  
  
4.  Dans la fenêtre Propriétés, tapez une valeur pour la propriété **Valeur par défaut facultative**. La définition de la propriété Valeur par défaut facultative d'un paramètre rend ce paramètre optionnel.  
  
    > [!NOTE]
    >  Les paramètres optionnels doivent être les derniers paramètres dans la liste de paramètres.  
  
##  <a name="ClassDetailsUsageNotes"></a> Notes d’utilisation de la fenêtre Détails de classe  
 Notez les conseils suivants pour utiliser la fenêtre Détails de classe.  
  
 **Cellules modifiables et cellules non modifiables**  
  
 Toutes les cellules de la fenêtre Détails de classe sont modifiables, à quelques exceptions près :  
  
-   Le type est en lecture seule quand, par exemple, il réside dans un assembly référencé (consultez [Affichage d’informations en lecture seule (Concepteur de classes)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a)). Lorsque vous sélectionnez la forme dans le Concepteur de classes, la fenêtre Détails de classe affiche ses détails en lecture seule.  
  
-   Pour les indexeurs, le nom est en lecture seule et le reste (type, modificateur, résumé) est modifiable.  
  
-   Tous les génériques ont des paramètres en lecture seule dans la fenêtre Détails de classe. Pour modifier un paramètre générique, modifiez son code source.  
  
-   Le nom du paramètre de type qui est défini sur un type générique est en lecture seule.  
  
-   Lorsque le code d'un type est rompu (non analysable), la fenêtre Détails de classe affiche le contenu du type en lecture seule.  
  
 **Fenêtre Détails de classe et code source**  
  
-   Vous pouvez consulter le code source en cliquant avec le bouton droit sur une forme de la fenêtre Détails de classe (ou du Concepteur de classes), puis en cliquant sur Afficher le code. Le fichier correspondant s'ouvre et le code source défile jusqu'à l'élément sélectionné.  
  
-   La modification du code source est immédiatement répercutée dans l'affichage des informations de signature dans le Concepteur de classes ou dans la fenêtre Détails de classe. Si la fenêtre Détails de classe est fermée à ce moment-là, les nouvelles informations ne seront visibles qu'à la prochaine ouverture.  
  
-   Lorsque le code d'un type est rompu (non analysable), la fenêtre Détails de classe affiche le contenu du type en lecture seule.  
  
 **Utilisation du Presse-papiers dans la fenêtre Détails de classe**  
  
 Vous pouvez copier ou couper des champs ou des lignes dans la fenêtre Détails de classe et les coller dans un autre type. Vous ne pouvez couper une ligne que si elle n'est pas en lecture seule. Lorsque vous collez la ligne, la fenêtre Détails de classe assigne un nouveau nom (dérivé du nom de la ligne copiée) afin d'éviter tout conflit.  
  
##  <a name="ReadOnlyInfo"></a> Affichage d’informations en lecture seule  
 Le Concepteur de classes et la fenêtre Détails de classe peuvent afficher les types (et les membres de types) des éléments suivants :  
  
-   projet contenant un diagramme de classes  
  
-   projet référencé d'un projet contenant un diagramme de classes  
  
-   assembly référencé d'un projet contenant un diagramme de classes  
  
 Dans les deux derniers cas, l'entité référencée (un type ou un membre) est en lecture seule dans le diagramme de classes qui la représente.  
  
 Tout ou partie (certains fichiers, par exemple) d'un projet peut être en lecture seule. Les cas les plus communs où un projet ou l'un de ses fichiers est en lecture seule se produisent quand le projet ou le fichier est sous contrôle du code source (et n'a pas été extrait), qu'il existe dans un assembly externe ou que le système d'exploitation considère les fichiers comme étant en lecture seule.  
  
 **Contrôle du code source**  
  
 Parce qu'un diagramme de classes est enregistré en tant que fichier dans un projet, vous devez extraire le projet pour sauvegarder toutes les modifications effectuées dans le Concepteur de classes ou dans la fenêtre Détails de classe.  
  
 **Projets en lecture seule**  
  
 Le projet peut être en lecture seule pour une autre raison que le contrôle du code source. La fermeture du projet affiche une boîte de dialogue qui demande si vous souhaitez remplacer le fichier projet, ignorer les modifications (aucun enregistrement) ou annuler l'opération de fermeture. Si vous faites le choix du remplacement, les fichiers projet sont remplacés et rendus accessibles en lecture-écriture. Le nouveau fichier du diagramme de classes est ajouté.  
  
 **Types en lecture seule**  
  
 Si vous essayez d’enregistrer un projet contenant un type dont le fichier de code source est en lecture seule, la boîte de dialogue **Enregistrement d’un fichier accessible en lecture seule** qui apparaît vous donne le choix entre enregistrer le fichier sous un nouveau nom (ou à un nouvel emplacement) ou remplacer le fichier en lecture seule. Si vous remplacez le fichier, la nouvelle copie n'est plus en lecture seule.  
  
 Si un fichier de code contient une erreur de syntaxe, les formes dédiées à l'affichage du code de ce fichier restent en lecture seule tant que l'erreur de syntaxe n'est pas résolue. Les formes affichent alors le texte en rouge et une icône de couleur rouge, accompagnée d'une info-bulle dont le texte est le suivant : « Le fichier de code source contient une erreur d'analyse. »  
  
 Un type référencé (comme un type .NET Framework), qui existe sous un autre nœud de projet ou sous un nœud d'assembly référencé, est signalé sur l'aire de conception du Concepteur de classes comme étant en lecture seule. Un type local, qui existe dans le projet que vous a ouvert, est en lecture-écriture, et sa forme sur l'aire de conception du Concepteur de classes est indiquée comme telle.  
  
 Les indexeurs sont en lecture-écriture dans le code et dans la fenêtre Détails de classe, mais le nom d'indexeur est en lecture seule.  
  
 Vous ne pouvez pas modifier de méthodes partielles à l'aide du Concepteur de classes ou de la fenêtre Détails de classe ; pour réaliser cette opération, vous devez utiliser l'éditeur de code.  
  
 Vous ne pouvez pas modifier de code C++ natif à l'aide du Concepteur de classes ou de la fenêtre Détails de Classe ; pour réaliser cette opération, vous devez utiliser l'éditeur de code.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Affichage des types et relations (Concepteur de classes)](../ide/viewing-types-and-relationships-class-designer.md)|Vous pouvez afficher les types, les membres et les relations existants dans un diagramme de classes.|  
|[Refactorisation des classes et des types (Concepteur de classes)](../ide/refactoring-classes-and-types-class-designer.md)|À l'aide de la refactorisation, vous pouvez aisément renommer le type et les membres de type. Vous pouvez également déplacer des membres entre les classes, fractionner une classe en classes partielles et implémenter des interfaces.|