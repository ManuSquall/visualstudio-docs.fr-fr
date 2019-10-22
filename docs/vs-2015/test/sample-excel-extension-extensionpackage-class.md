---
title: 'Exemple d’extension Excel : classe ExtensionPackage | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1c1f4c746fa505b50bab9caa7a516a2abc77f69
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672210"
---
# <a name="sample-excel-extension-extensionpackage-class"></a>Exemple d'extension Excel : classe ExtensionPackage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette classe étend la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> et fournit le point d’entrée pour un test codé de l’interface utilisateur qui teste une feuille de calcul [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].

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
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> [l’extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre en charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
