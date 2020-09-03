---
title: Exemple d’extension du test codé de l’interface utilisateur pour Excel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672230"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Exemple d’extension du test codé de l’interface utilisateur pur Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le composant d’extension de l’exemple s’exécute dans le processus de test codé de l’interface utilisateur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] et entretient une sorte de lien hiérarchique avec la classe `ExtensionPackage` située à la base. Les classes `TechnologyManager`, `ActionFilter` et `PropertyProvider` sont au niveau suivant, les éléments de contrôle étant au niveau supérieur.

 ![Architecture d’extension de test Excel](../test/media/excel-extarch.png "Excel_ExtArch") Architecture d’extension Excel

## <a name="extension-points"></a>Points d’extension
 Ces classes représentent les points d’extension implémentés dans l’exemple pour activer le test codé de l’interface utilisateur pour [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

### <a name="extensionpackage"></a>ExtensionPackage
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, il s’agit du point d’entrée pour l’extension de test codé de l’interface utilisateur. L’implémentation de cette classe abstraite permet au framework de test codé de l’interface utilisateur d’accéder de manière interne à votre gestionnaire de technologies de test d’IU personnalisé, votre fournisseur de propriétés de test d’IU et votre filtre d’action de test d’IU pour tester la nouvelle IU. Pour plus d’informations, consultez [ExtensionPackage, classe](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, cette classe fournit un gestionnaire de technologies pour l’enregistrement et la lecture de test. Pour plus d’informations, consultez [TechnologyManager, classe](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Héritée de la classe [UITestActionFilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) , cette classe fournit une classe de base permettant d’agréger les résultats d’actions de test similaires en un résultat de test unique. Pour plus d’informations, consultez [ActionFilter, classe](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Éléments de technologie
 Une classe de base héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> fournit la base des éléments de technologie de vos tests d’interface utilisateur qui peuvent être enregistrés et lus. Pour plus d’informations, consultez [Classes d’éléments](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, cette classe fournit une classe de base prenant en charge les propriétés des éléments d’interface utilisateur pour l’enregistrement et la lecture des tests. Pour plus d’informations, consultez [PropertyProvider, classe](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Classe ExtensionPackage](../test/sample-excel-extension-extensionpackage-class.md)
- [Classe TechnologyManager](../test/sample-excel-extension-technologymanager-class.md)
- [Classe ActionFilter](../test/sample-excel-extension-actionfilter-class.md)
- [Classes d’éléments](../test/sample-excel-extension-element-classes.md)
- [Classe PropertyProvider](../test/sample-excel-extension-propertyprovider-class.md)
