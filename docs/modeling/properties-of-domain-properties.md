---
title: Propriétés des propriétés de domaine
description: Découvrez comment une propriété de domaine est une fonctionnalité d’un élément de modèle qui peut contenir une valeur, et comment les propriétés de domaine sont répertoriées dans la zone classe de domaine du diagramme.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2f026f62c5440b48b04d05e080515c47dd11979
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390644"
---
# <a name="properties-of-domain-properties"></a>Propriétés des propriétés de domaine
Une *propriété de domaine* est une fonctionnalité d’un élément de modèle qui peut contenir une valeur. Par exemple, la classe de domaine `Person` pourrait avoir des propriétés `Name` et `BirthDate`. Dans la définition DSL, les propriétés de domaine sont énumérées dans la zone de classe de domaine sur le diagramme et sous la classe de domaine dans l'Explorateur DSL. Pour plus d’informations, consultez [comment définir un langage de Domain-Specific](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Le mot « propriété » a deux utilisations. Une *propriété de domaine* est une fonctionnalité que vous définissez sur une classe de domaine. En revanche, de nombreux éléments d’un DSL ont des *Propriétés*, qui sont répertoriées dans la fenêtre **Propriétés** dans la définition DSL. Par exemple, chaque propriété de domaine possède un jeu de propriétés qui sont décrites dans cette rubrique.

 Au moment de l'exécution, quand un utilisateur crée des instances de la classe de domaine, les valeurs des propriétés de domaine sont visibles dans la fenêtre Propriétés et peuvent être affichées sur les formes.

 La plupart des propriétés de domaine sont implémentées en tant que propriétés CLR ordinaires. Toutefois, du point de vue de la programmation, les propriétés de domaine ont des fonctionnalités enrichies par rapport aux propriétés de programme ordinaires :

- Vous pouvez définir des règles et des événements qui surveillent l'état d'une propriété. Pour plus d’informations, consultez [réponse aux modifications et propagation](../modeling/responding-to-and-propagating-changes.md).

- Les transactions aident à prévenir les états incohérents. Pour plus d’informations, consultez [navigation et mise à jour d’un modèle dans le code de programme](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Quand vous sélectionnez une propriété de domaine dans un diagramme ou dans l'Explorateur DSL, les éléments suivants sont visibles dans la fenêtre Propriétés. Pour plus d’informations sur l’utilisation de ces éléments, consultez [personnalisation et extension d’un langage de Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Propriété|Description|Valeur par défaut|
|-|-|-|
|**Description**|Description utilisée pour documenter l'interface utilisateur du concepteur généré.|\<none>|
|**Nom complet**|Non affiché dans le concepteur généré pour cette propriété de domaine. Il peut contenir des espaces et une ponctuation, par exemple « Titre du morceau ».|\<none>|
|**Element Name Provider**|Applicable uniquement si vous avez affecté la valeur `Is Element Name` à `true`. Vous pouvez écrire du code qui fournit un nom pour un nouvel élément d'une classe de domaine et qui remplace le comportement par défaut.<br /><br /> Dans un fichier de code dans le projet DSL, créez une classe dérivée de <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider>.<br /><br /> Ensuite, dans l'Explorateur DSL, cliquez avec le bouton droit sur la racine de la solution DSL, puis cliquez sur Ajouter un type externe. Entrez le nom de votre classe.<br /><br /> Sélectionnez de nouveau cette propriété de domaine et sélectionnez le nom de la classe dans la liste déroulante.|\<none>|
|**Getter Access Modifier**|Niveau d'accès de la classe de domaine (`public` ou `internal`). Contrôle l'étendue selon laquelle le code de programme peut accéder à la propriété.|`public`|
|**Mot clé d’aide**|Mot clé facultatif servant à indexer l'aide F1 pour cette propriété de domaine.|\<none>|
|**Is Browsable**|Si `True`, la propriété de domaine est présentée à l'utilisateur dans la fenêtre de propriétés quand des modèles de cette solution DSL sont ouverts.<br /><br /> Si `False`, la propriété de domaine est masquée dans l'interface utilisateur.<br /><br /> Si vous souhaitez que la propriété de domaine soit visible mais en lecture seule, définissez **est lecture seule de l’interface utilisateur**.|`True`|
|**Is Element Name**|Si `True`, cette propriété de domaine est affichée comme nom de son élément de modèle dans l'Explorateur DSL.<br /><br /> Les nouveaux éléments de modèle reçoivent une valeur par défaut unique pour cette propriété. Si vous souhaitez contrôler la façon dont ces valeurs sont générées, définissez le **fournisseur de nom d’élément**.|`False`|
|**Is UI Read Only**|Si `True`, la valeur de la propriété de domaine ne peut pas être modifiée à l'aide de l'interface utilisateur. Elle peut quand même être définie par des programmes et sera visible dans la fenêtre Propriétés.<br /><br /> Si vous souhaitez masquer la propriété de domaine de l’utilisateur, Set **peut être exploré**. Si vous souhaitez contrôler l’accès par les programmes, définissez le **modificateur d’accès Setter**.|`False`|
|**Type**|Genre de propriété de domaine (`Normal`, `Calculated` ou `CustomStorage`). Pour plus d’informations, consultez [Propriétés de stockage calculées et personnalisées](../modeling/calculated-and-custom-storage-properties.md).|`Normal`|
|**Nom**|Nom de cette propriété de domaine. Il doit s’agir d’un identificateur valide, par exemple **titremorceau**.|\<none>|
|**Remarques**|Remarques informelles associées à cette propriété de domaine.|\<none>|
|**Setter Access Modifier**|Modificateur d'accès pour la méthode Setter. Contrôle l'étendue selon laquelle le code de programme peut définir la propriété.|`public`|
|**Type**|Type de propriété. Pour ajouter à la liste des types disponibles, cliquez avec le bouton droit sur la racine du DSL dans l’Explorateur DSL, puis cliquez sur **Ajouter un type externe**.|`String`|

## <a name="see-also"></a>Voir aussi

- [Glossaire des Outils Domain-Specific Language](/previous-versions/bb126564(v=vs.100))