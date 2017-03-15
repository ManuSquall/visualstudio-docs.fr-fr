---
title: "Exemple d&#39;extension Excel&#160;: classe ExtensionPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 9
---
# Exemple d&#39;extension Excel&#160;: classe ExtensionPackage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Cette classe étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> et fournit le point d'entrée d'un test codé de l'interface utilisateur qui teste une feuille de calcul [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Attribut d'assembly  
 Le fichier commence par un attribut d'assembly qui identifie l'assembly comme une extension de test d'IU.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Cet attribut déclare le nom de la classe de base, le nom de la classe du package et le nom de classe complet pour la classe de package d'extension personnalisée.  
  
## Propriétés simples  
 Cette classe possède des propriétés qui fournissent des valeurs utilisées par l'infrastructure de test codé de l'interface utilisateur permettant d'identifier et de décrire l'extension et l'assembly.  Pour plus d'informations, consultez les commentaires du code.  
  
## Méthode GetService  
 La méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> est le point d'entrée unique utilisé par l'infrastructure de test codé de l'interface utilisateur pour accéder au gestionnaire de technologies, au fournisseur de propriétés et au filtre d'actions, comme cela est identifié par la classe de base de chaque objet.  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Extension des tests codés de l'interface utilisateur t enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)