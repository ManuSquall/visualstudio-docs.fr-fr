---
title: Propriétés des propriétés de domaine | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain properties
ms.assetid: a9471562-d6f2-46bf-9872-e0d66ba03150
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fa5e2f46f3fa5cce9a795c2353148d2bd3f47351
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49293109"
---
# <a name="properties-of-domain-properties"></a>Propriétés des propriétés de domaine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un *de propriété de domaine* est une fonctionnalité d’un élément de modèle qui peut contenir une valeur. Par exemple, la classe de domaine `Person` pourrait avoir des propriétés `Name` et `BirthDate`. Dans la définition DSL, les propriétés de domaine sont énumérées dans la zone de classe de domaine sur le diagramme et sous la classe de domaine dans l'Explorateur DSL. Pour plus d’informations, consultez [comment définir un langage spécifique à un domaine](../modeling/how-to-define-a-domain-specific-language.md).  
  
> [!NOTE]
>  Le mot « propriété » a deux utilisations. Un *de propriété de domaine* est une fonctionnalité que vous définissez sur une classe de domaine. En revanche, ont de nombreux éléments d’une solution DSL *propriétés*, qui sont répertoriées dans le **propriétés** fenêtre dans la définition DSL. Par exemple, chaque propriété de domaine possède un jeu de propriétés qui sont décrites dans cette rubrique.  
  
 Au moment de l'exécution, quand un utilisateur crée des instances de la classe de domaine, les valeurs des propriétés de domaine sont visibles dans la fenêtre Propriétés et peuvent être affichées sur les formes.  
  
 La plupart des propriétés de domaine sont implémentées en tant que propriétés CLR ordinaires. Toutefois, du point de vue de la programmation, les propriétés de domaine ont des fonctionnalités enrichies par rapport aux propriétés de programme ordinaires :  
  
-   Vous pouvez définir des règles et des événements qui surveillent l'état d'une propriété. Pour plus d’informations, consultez [réponse en cours à et propagation des modifications](../modeling/responding-to-and-propagating-changes.md).  
  
-   Les transactions aident à prévenir les états incohérents. Pour plus d’informations, consultez [navigation et la mise à jour un modèle dans le Code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
 Quand vous sélectionnez une propriété de domaine dans un diagramme ou dans l'Explorateur DSL, les éléments suivants sont visibles dans la fenêtre Propriétés. Pour plus d’informations sur l’utilisation de ces éléments, consultez [personnalisation et extension d’un langage spécifique à un domaine](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Propriété|Description|Valeur par défaut|  
|--------------|-----------------|-------------------|  
|**Description**|Description utilisée pour documenter l'interface utilisateur du concepteur généré.|\<Aucun >|  
|**Nom d’affichage**|Non affiché dans le concepteur généré pour cette propriété de domaine. Il peut contenir des espaces et une ponctuation, par exemple « Titre du morceau ».|\<Aucun >|  
|**ELEMENT Name Provider**|Applicable uniquement si vous avez affecté la valeur `Is Element Name` à `true`. Vous pouvez écrire du code qui fournit un nom pour un nouvel élément d'une classe de domaine et qui remplace le comportement par défaut.<br /><br /> Dans un fichier de code dans le projet DSL, créez une classe dérivée de <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Ensuite, dans l'Explorateur DSL, cliquez avec le bouton droit sur la racine de la solution DSL, puis cliquez sur Ajouter un type externe. Entrez le nom de votre classe.<br /><br /> Sélectionnez de nouveau cette propriété de domaine et sélectionnez le nom de la classe dans la liste déroulante.|\<Aucun >|  
|**Modificateur d’accès getter**|Niveau d'accès de la classe de domaine (`public` ou `internal`). Contrôle l'étendue selon laquelle le code de programme peut accéder à la propriété.|`public`|  
|**Mot clé d’aide**|Mot clé facultatif servant à indexer l'aide F1 pour cette propriété de domaine.|\<Aucun >|  
|**Peut être exploré**|Si `True`, la propriété de domaine est présentée à l'utilisateur dans la fenêtre de propriétés quand des modèles de cette solution DSL sont ouverts.<br /><br /> Si `False`, la propriété de domaine est masquée dans l'interface utilisateur.<br /><br /> Si vous souhaitez que la propriété de domaine visible mais en lecture seule, définissez **Is UI Read Only**.|`True`|  
|**Est le nom de l’élément**|Si `True`, cette propriété de domaine est affichée comme nom de son élément de modèle dans l'Explorateur DSL.<br /><br /> Les nouveaux éléments de modèle reçoivent une valeur par défaut unique pour cette propriété. Si vous souhaitez contrôler la façon dont ces valeurs sont générées, définissez **Element Name Provider**.|`False`|  
|**Est l’interface utilisateur en lecture seule**|Si `True`, la valeur de la propriété de domaine ne peut pas être modifiée à l'aide de l'interface utilisateur. Elle peut quand même être définie par des programmes et sera visible dans la fenêtre Propriétés.<br /><br /> Si vous souhaitez masquer la propriété de domaine à partir de l’utilisateur, définissez **Is Browsable**. Si vous souhaitez contrôler l’accès par des programmes, définissez **Setter Access Modifier**.|`False`|  
|**Type**|Genre de propriété de domaine (`Normal`, `Calculated` ou `CustomStorage`). Pour plus d’informations, consultez [calculées et les propriétés de stockage personnalisé](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|  
|**Name**|Nom de cette propriété de domaine. Il doit être un identificateur valid, par exemple **Titremorceau**.|\<Aucun >|  
|**Notes**|Remarques informelles associées à cette propriété de domaine.|\<Aucun >|  
|**Modificateur d’accès Setter**|Modificateur d'accès pour la méthode Setter. Contrôle l'étendue selon laquelle le code de programme peut définir la propriété.|`public`|  
|**Type**|Type de propriété. Pour ajouter à la liste des types disponibles, avec le bouton droit de la racine de la solution DSL dans l’Explorateur DSL, puis cliquez sur **ajouter un Type externe**.|`String`|  
  
## <a name="see-also"></a>Voir aussi  
 [Glossaire des outils Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



