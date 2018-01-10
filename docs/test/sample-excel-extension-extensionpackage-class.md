---
title: "Exemple d’extension Excel : classe ExtensionPackage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 3603746325be5feff231d5e2538282f7bf6d6893
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Exemple d'extension Excel : classe ExtensionPackage
Cette classe étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> et fournit le point d’entrée pour un test codé de l’interface utilisateur qui teste une feuille de calcul [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## <a name="assembly-attribute"></a>Attribut d’assembly  
 Le fichier commence par un attribut d’assembly qui identifie l’assembly en tant qu’extension de test d’IU.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Cet attribut déclare le nom de la classe de base, le nom de la classe de package et le nom de classe complet de la classe de package d’extension personnalisée.  
  
## <a name="simple-properties"></a>Propriétés simples  
 Cette classe a des propriétés qui fournissent des valeurs utilisées par le framework de test codé de l’interface utilisateur pour identifier et décrire l’extension et l’assembly. Pour plus d’informations, consultez les commentaires de code.  
  
## <a name="getservice-method"></a>GetService, méthode  
 La méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> est le point d’entrée unique utilisé par le framework de test codé de l’interface utilisateur pour accéder au gestionnaire de technologies, au fournisseur de propriétés et au filtre d’action, tels qu’ils sont identifiés par la classe de base de chaque objet.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
