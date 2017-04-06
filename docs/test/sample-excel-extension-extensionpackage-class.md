---
title: "Exemple d’extension Excel : classe ExtensionPackage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 20e3ac96d5b12002b11a9e93b413c48738f57153
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-extensionpackage-class"></a>Exemple d’extension Excel : classe ExtensionPackage
Cette classe étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> et fournit le point d’entrée d’un test codé de l’interface utilisateur qui teste une feuille de calcul [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
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
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre en charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

