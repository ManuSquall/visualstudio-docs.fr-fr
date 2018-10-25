---
title: 'Exemple d’extension Excel : classes d’éléments | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb5085bdd9a79330f7c4f73fb39993af63eb0a78
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811944"
---
# <a name="sample-excel-extension-element-classes"></a>Exemple d'extension Excel : classes d'éléments
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L’extension utilise des classes dérivées de <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> et qui représentent le contrôle Worksheet et le contrôle Cell dans [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)].  
  
 L’élément de base de cette extension est `ExcelElement`. La classe `ExcelWorksheetElement` et la classe `ExcelCellElement` héritent de cet élément  
  
## <a name="element-and-elementinformation-classes"></a>Element et ElementInformation, classes  
 `Element` est la classe de base pour tous les éléments d’interface utilisateur pour l’extension Excel. Elle hérite de la classe <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>. `ElementInformation` est la classe de base des classes d’informations des éléments dans l’exemple. Elle n’a aucun membre.  
  
#### <a name="simple-properties-and-methods"></a>Propriétés et méthodes simples  
 Ces membres retournent des valeurs simples, telles que la valeur de la propriété `Name` ou la valeur de la propriété `ClassName`. De plus, le code est clair et facile à lire. Certaines valeurs sont retournées à l’aide de la classe `Utility`, qui est abordée plus tard. D’autres retournent `null` en raison de leur manque de pertinence dans cet exemple d’extension. Deux membres sont plus intéressants que les autres : la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> et la méthode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A>.  
  
#### <a name="queryid-property"></a>QueryId, propriété  
 Cette propriété retourne une condition constituée de paires nom-valeur de propriété qui identifient le contrôle de manière unique pendant la lecture. Pour chaque classe de contrôle dérivée, le développeur doit remplacer cette propriété afin de retourner un objet <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> dont le framework peut se servir pour rechercher le contrôle dans l’interface utilisateur.  
  
#### <a name="cacheproperties-method"></a>CacheProperties, méthode  
 Cette méthode est appelée par le framework de test au cours du processus d’enregistrement pour indiquer à l’élément d’enregistrer un instantané des propriétés importantes. Cela permet de garder les propriétés disponibles même quand le contrôle d’IU réel n’est plus à l’écran.  
  
## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement et WorksheetInformation, classes  
 La classe `WorksheetElement` représente une feuille de calcul Excel dans le framework de test et hérite de la classe de base `Element`. Trois propriétés sont remplacées pour fournir des informations spécifiques sur l’objet de feuille de calcul Excel : <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A> et <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>.  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> est également appliqué à cette classe pour la rendre visible par COM.  
  
 La classe `WorksheetInformation` représente les informations relatives à une feuille de calcul Excel. Elle n’a qu’un seul membre, la propriété `SheetName`, ce qui est suffisant pour cet exemple.  
  
## <a name="cellelement-and-cellinformation-classes"></a>CellElement et CellInformation, classes  
 La classe `CellElement` représente une cellule Excel et hérite de la classe de base `Element`. Le seul membre remplacé est la propriété <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>, qui retourne un <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> qui utilise les propriétés `RowIndex` et `ColumnIndex` pour identifier la cellule.  
  
## <a name="utilities-and-excelutilities-classes"></a>Utilities et ExcelUtilities, classes  
 La classe `ExcelUtilities` interne fournit certaines valeurs constantes, notamment le nom de technologie, et une méthode qui détermine si le handle de fenêtre fourni représente une feuille de calcul Excel.  
  
 La classe `Utilities` a des méthodes d’assistance qui retournent toutes sortes d’informations sur l’IU. Certaines méthodes utilisent des appels directs aux DLL du système externe, par exemple **USER32.DLL** et **OLEACC.DLL**, pour obtenir des handles de fenêtres à partir de l’IU<strong>.</strong>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>   
 [Extension des tests codés de l’interface utilisateur et des enregistrements des actions pour prendre charge Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



