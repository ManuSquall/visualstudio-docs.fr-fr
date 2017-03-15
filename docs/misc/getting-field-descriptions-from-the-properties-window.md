---
title: "Obtenir des descriptions de champs &#224; partir de la fen&#234;tre Propri&#233;t&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fenêtre Propriétés, descriptions de champs"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Obtenir des descriptions de champs &#224; partir de la fen&#234;tre Propri&#233;t&#233;s
En bas de la fenêtre **Propriétés**, une zone de description affiche des informations relatives au champ de propriété sélectionné. Cette fonctionnalité est activée par défaut. Si vous voulez masquer le champ de description, cliquez avec le bouton droit sur la fenêtre **Propriétés** et cliquez sur **Description**. Cette action supprime également la coche à côté du titre **Description** dans la fenêtre de menu. Vous pouvez afficher le champ à nouveau en suivant la même procédure pour réactiver **Description**.  
  
 Les informations du champ de description proviennent de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Chaque méthode, interface, coclasse, etc. peut avoir un attribut `helpstring` non localisé dans la bibliothèque de types. La fenêtre **Propriétés** récupère la chaîne à partir de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### Pour spécifier des chaînes d’aide localisées  
  
1.  Ajoutez l’attribut `helpstringdll` à l’instruction library dans la bibliothèque de types \(`typelib`\).  
  
    > [!NOTE]
    >  Cette étape est facultative si la bibliothèque de types se trouve dans un fichier de bibliothèque d’objets \(.olb\).  
  
2.  Spécifiez des attributs `helpstringcontext` pour les chaînes. Vous pouvez également spécifier des attributs `helpstring`.  
  
     Ces attributs sont distincts des attributs `helpfile` et `helpcontext` qui sont contenus dans les vraies rubriques d’aide du fichier .chm.  
  
 Pour récupérer les informations de description à afficher pour le nom de la propriété mise en surbrillance, la fenêtre **Propriétés** appelle <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pour la propriété sélectionnée, en spécifiant l’attribut `lcid` souhaité pour la chaîne de sortie. En interne, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> recherche le fichier .dll spécifié dans l’attribut `helpstringdll` et appelle `DLLGetDocumentation` sur ce fichier .dll avec le contexte spécifié et l’attribut `lcid`.  
  
 La signature et l’implémentation de `DLLGetDocumentation` sont les suivantes :  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 La fonction `DLLGetDocumentation` doit être une exportation définie dans le fichier .def pour la DLL.  
  
 En interne, un fichier .olb est créé, qui est effectivement une DLL. Cette DLL contient une ressource, le fichier de bibliothèque de types \(.tlb\) et une fonction exportée, `DLLGetDocumentation`.  
  
 Dans le cas des fichiers .olb, l’attribut `helpstringdll` est facultatif, car il s’agit du même fichier qui contient le fichier .tlb lui\-même.  
  
 Par conséquent, pour que des chaînes s’affichent dans le volet **Descriptions**, vous devez au moins spécifier l’attribut `helpstring` dans la bibliothèque de types. Si vous voulez que ces chaînes soient localisées, vous devez spécifier l’attribut `helpstringdll` \(facultatif\) et l’attribut `helpstringcontext` \(obligatoire\), et implémenter `DLLGetDocumentation`.  
  
 Aucune autre interface ne doit être implémentée lors de la localisation d’informations par le biais de l’attribut `helpstringcontext` d’idl et `DLLGetDocumentation`.  
  
 Pour obtenir le nom et la description localisés d’une propriété, vous pouvez aussi implémenter <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Pour plus d’informations sur l’implémentation de cette méthode, consultez [Interfaces et les champs de la fenêtre Propriétés](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Interfaces et les champs de la fenêtre Propriétés](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Étendre les propriétés](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)