---
title: "Exemple d'extension Excel : classe ExtensionPackage"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: sample
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43234161979df9190daddeec168e7a40a14db498
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
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

- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
