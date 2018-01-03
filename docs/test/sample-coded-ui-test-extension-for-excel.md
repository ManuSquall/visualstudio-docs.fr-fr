---
title: "Exemple d’extension du test codé de l’interface utilisateur pour Excel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: "13"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 11a1c2a09b1a41f0f60879bdaabdf79696a0199e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Exemple d’extension du test codé de l’interface utilisateur pur Excel
Le composant d’extension de l’exemple s’exécute dans le processus de test codé de l’interface utilisateur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] et entretient une sorte de lien hiérarchique avec la classe `ExtensionPackage` située à la base. Les classes `TechnologyManager`, `ActionFilter` et `PropertyProvider` sont au niveau suivant, les éléments de contrôle étant au niveau supérieur.  
  
 ![Architecture d’extension de test Excel](../test/media/excel_extarch.png "Excel_ExtArch")  
Architecture d’extension Excel  
  
## <a name="extension-points"></a>Points d’extension  
 Ces classes représentent les points d’extension implémentés dans l’exemple pour activer le test codé de l’interface utilisateur pour [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>, il s’agit du point d’entrée pour l’extension de test codé de l’interface utilisateur. L’implémentation de cette classe abstraite permet au framework de test codé de l’interface utilisateur d’accéder de manière interne à votre gestionnaire de technologies de test d’IU personnalisé, votre fournisseur de propriétés de test d’IU et votre filtre d’action de test d’IU pour tester la nouvelle IU. Pour plus d’informations, consultez [ExtensionPackage, classe](../test/sample-excel-extension-extensionpackage-class.md).  
  
### <a name="technologymanager"></a>TechnologyManager  
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>, cette classe fournit un gestionnaire de technologies pour l’enregistrement et la lecture de test. Pour plus d’informations, consultez [TechnologyManager, classe](../test/sample-excel-extension-technologymanager-class.md).  
  
### <a name="actionfilter"></a>ActionFilter  
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>, cette classe fournit une classe de base permettant d’agréger les résultats d’actions de test similaires en un résultat de test unique. Pour plus d’informations, consultez [ActionFilter, classe](../test/sample-excel-extension-actionfilter-class.md).  
  
### <a name="technology-elements"></a>Éléments de technologie  
 Une classe de base héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> fournit la base des éléments de technologie de vos tests d’interface utilisateur qui peuvent être enregistrés et lus. Pour plus d’informations, consultez [Classes d’éléments](../test/sample-excel-extension-element-classes.md).  
  
### <a name="propertyprovider"></a>PropertyProvider  
 Héritée de la classe <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>, cette classe fournit une classe de base prenant en charge les propriétés des éléments d’interface utilisateur pour l’enregistrement et la lecture des tests. Pour plus d’informations, consultez [PropertyProvider, classe](../test/sample-excel-extension-propertyprovider-class.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage, classe](../test/sample-excel-extension-extensionpackage-class.md)   
 [TechnologyManager, classe](../test/sample-excel-extension-technologymanager-class.md)   
 [ActionFilter, classe](../test/sample-excel-extension-actionfilter-class.md)   
 [Classes d’éléments](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider, classe](../test/sample-excel-extension-propertyprovider-class.md)
