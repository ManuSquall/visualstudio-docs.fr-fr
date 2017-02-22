---
title: "Propri&#233;t&#233;s des propri&#233;t&#233;s de domaine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "langage spécifique à un domaine, propriétés de domaine"
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 24
---
# Propri&#233;t&#233;s des propri&#233;t&#233;s de domaine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Une *propriété de domaine* est une fonctionnalité d'un élément de domaine qui peut contenir une valeur.  Par exemple, la classe de domaine `Person` pourrait avoir des propriétés `Name` et `BirthDate`.  Dans la définition DSL, les propriétés de domaine sont énumérées dans la zone de classe de domaine sur le diagramme et sous la classe de domaine dans l'Explorateur DSL.  Pour plus d'informations, consultez [Comment : définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Le mot « propriété » a deux utilisations.  Une *propriété de domaine* est une fonctionnalité que vous définissez sur une classe de domaine.  Par contraste, de nombreux éléments d'une solution DSL ont des *propriétés*, qui sont énumérées dans la fenêtre **Propriétés** dans la définition DSL.  Par exemple, chaque propriété de domaine possède un jeu de propriétés qui sont décrites dans cette rubrique.  
  
 Au moment de l'exécution, quand un utilisateur crée des instances de la classe de domaine, les valeurs des propriétés de domaine sont visibles dans la fenêtre Propriétés et peuvent être affichées sur les formes.  
  
 La plupart des propriétés de domaine sont implémentées en tant que propriétés CLR ordinaires.  Toutefois, du point de vue de la programmation, les propriétés de domaine ont des fonctionnalités enrichies par rapport aux propriétés de programme ordinaires :  
  
-   Vous pouvez définir des règles et des événements qui surveillent l'état d'une propriété.  Pour plus d'informations, consultez [Propagation et réponse aux modifications en attente](../modeling/responding-to-and-propagating-changes.md).  
  
-   Les transactions aident à prévenir les états incohérents.  Pour plus d'informations, consultez [Navigation et mise à jour d'un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Quand vous sélectionnez une propriété de domaine dans un diagramme ou dans l'Explorateur DSL, les éléments suivants sont visibles dans la fenêtre Propriétés.  Pour plus d'informations sur l'utilisation de ces éléments, consultez [Personnalisation et extension d'un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Valeur par défaut|  
|---------------|-----------------|-----------------------|  
|**Description**|Description utilisée pour documenter l'interface utilisateur du concepteur généré.|\<aucune\>|  
|**Display Name**|Non affiché dans le concepteur généré pour cette propriété de domaine.  Il peut contenir des espaces et une ponctuation, par exemple « Titre du morceau ».|\<aucune\>|  
|**Element Name Provider**|Applicable uniquement si vous avez affecté la valeur `true` à `Is Element Name`.  Vous pouvez écrire du code qui fournit un nom pour un nouvel élément d'une classe de domaine et qui remplace le comportement par défaut.<br /><br /> Dans un fichier de code dans le projet DSL, créez une classe dérivée de <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Ensuite, dans l'Explorateur DSL, cliquez avec le bouton droit sur la racine de la solution DSL, puis cliquez sur Ajouter un type externe.  Entrez le nom de votre classe.<br /><br /> Sélectionnez de nouveau cette propriété de domaine et sélectionnez le nom de la classe dans la liste déroulante.|\<aucune\>|  
|**Getter Access Modifier**|Niveau d'accès de la classe de domaine \(`public` ou `internal`\).  Contrôle l'étendue selon laquelle le code de programme peut accéder à la propriété.|`public`|  
|**Help Keyword**|Mot clé facultatif servant à indexer l'aide F1 pour cette propriété de domaine.|\<aucune\>|  
|**Is Browsable**|Si `True`, la propriété de domaine est présentée à l'utilisateur dans la fenêtre de propriétés quand des modèles de cette solution DSL sont ouverts.<br /><br /> Si `False`, la propriété de domaine est masquée dans l'interface utilisateur.<br /><br /> Si vous souhaitez rendre la propriété de domaine visible mais en lecture seule, définissez **Is UI Read Only**.|`True`|  
|**Is Element Name**|Si `True`, cette propriété de domaine est affichée comme nom de son élément de modèle dans l'Explorateur DSL.<br /><br /> Les nouveaux éléments de modèle reçoivent une valeur par défaut unique pour cette propriété.  Si vous voulez contrôler la manière dont ces valeurs sont générées, définissez **Element Name Provider**.|`False`|  
|**Is UI Read Only**|Si `True`, la valeur de la propriété de domaine ne peut pas être modifiée à l'aide de l'interface utilisateur.  Elle peut quand même être définie par des programmes et sera visible dans la fenêtre Propriétés.<br /><br /> Si vous souhaitez masquer la propriété de domaine aux yeux de l'utilisateur, définissez **Is Browsable**.  Si vous voulez contrôler l'accès par les programmes, définissez **Setter Access Modifier**.|`False`|  
|**Kind**|Genre de propriété de domaine \(`Normal`, `Calculated` ou `CustomStorage`\).  Pour plus d'informations, consultez [Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Nom**|Nom de cette propriété de domaine.  Il doit s'agir d'un identificateur valide, par exemple TitreMorceau.|\<aucune\>|  
|**Remarques**|Remarques informelles associées à cette propriété de domaine.|\<aucune\>|  
|**Setter Access Modifier**|Modificateur d'accès pour la méthode Setter.  Contrôle l'étendue selon laquelle le code de programme peut définir la propriété.|`public`|  
|**Type**|Type de propriété.  Pour ajouter à la liste de types disponibles, cliquez avec le bouton droit sur la racine de la solution DSL dans l'Explorateur DSL, puis cliquez sur **Ajouter un type externe**.|`String`|  
  
## Voir aussi  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/fr-fr/ca5e84cb-a315-465c-be24-76aa3df276aa)