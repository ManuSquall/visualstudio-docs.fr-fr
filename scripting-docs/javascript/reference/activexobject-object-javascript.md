---
title: "ActiveXObject, objet (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ActiveXObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ActiveXObject (objet)"
  - "objets Automation, objets ActiveXObject"
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# ActiveXObject, objet (JavaScript)
Active et retourne une référence vers un objet Automation.  
  
 Cet objet est utilisé uniquement pour instancier des objets Automation, et n'a aucun membre.  
  
> [!WARNING]
>  Cet objet est une extension Microsoft et est pris en charge uniquement dans Internet Explorer, pas dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Syntaxe  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## Paramètres  
 `newObj`  
 Obligatoire.  Nom de la variable à laquelle l'objet `ActiveXObject` est assigné.  
  
 `servername`  
 Obligatoire.  Nom de l'application qui fournit l'objet.  
  
 `typename`  
 Obligatoire.  Type ou classe de l'objet à créer.  
  
 `location`  
 Facultatif.  Nom du serveur réseau au niveau duquel l'objet doit être créé.  
  
## Notes  
 Les serveurs Automation fournissent au moins un type d'objet.  Par exemple, une application de traitement de texte peut fournir un objet application, un objet document et un objet barre d'outils.  
  
 Vous pouvez identifier les valeurs `servername.typename` sur un PC hôte dans la clé de Registre `HKEY_CLASSES_ROOT`.  Par exemple, voici quelques exemples des valeurs que vous pouvez trouver là, en fonction des programmes installés :  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  Les objets ActiveX peuvent présenter des problèmes de sécurité.  Pour utiliser `ActiveXObject`, vous devrez régler les paramètres de sécurité dans Internet Explorer pour la zone de sécurité appropriée.  Par exemple, pour la zone Intranet, vous devez généralement modifier un paramètre personnalisé pour « initialiser et générer un script des contrôles ActiveX non marqués comme sécurisés pour les scripts ».  
  
 Pour identifier les membres d'un objet Automation que vous pouvez utiliser dans votre code, vous devrez peut\-être utiliser un explorateur d'objets COM, tel que l'[Explorateur d'objets OLE\/COM](http://msdn.microsoft.com/library/d0kh9f4c.aspx), si aucune documentation de référence n'est disponible pour l'objet Automation.  
  
 Pour créer un objet Automation, assignez le nouvel objet `ActiveXObject` à une variable objet :  
  
```javascript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 Ce code démarre l'application qui crée l'objet \(dans ce cas, une feuille de calcul Microsoft Excel\).  Une fois l'objet créé, vous le référencez dans le code à l'aide de la variable objet que vous avez définie.  Dans l'exemple suivant, vous pouvez accéder aux propriétés et aux méthodes du nouvel objet à l'aide de la variable objet `ExcelSheet` et d'autres objets Excel, notamment l'objet Application et la collection ActiveSheet.Cells.  
  
```javascript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## Configuration requise  
 Pris en charge dans les modes de document suivants : Quirks, Internet Explorer 6 \(mode standard\), Internet Explorer 7 \(mode standard\), Internet Explorer 8 \(mode standard\), Internet Explorer 9 \(mode standard\), Internet Explorer 10 \(mode standard\) et Internet Explorer 11 \(mode standard\).  Non pris en charge dans les applications [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  Consultez [Informations sur la version](../../javascript/reference/javascript-version-information.md).  
  
> [!NOTE]
>  La création d'un `ActiveXObject` sur un serveur distant n'est pas prise en charge dans [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] ou version ultérieure.  
  
## Voir aussi  
 [Fonction GetObject](../../javascript/reference/getobject-function-javascript.md)   
 [Authentification unique à l'aide de l'exemple d'application Magic de HTML5\/WCF](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)