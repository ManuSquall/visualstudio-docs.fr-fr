---
title: Obtention de Descriptions de champs à partir de la fenêtre Propriétés | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 5c7ae9cd659fb317ff74639fa20659296e126d04
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47501401"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Obtenir des descriptions de champs à partir de la fenêtre Propriétés
En bas de la fenêtre **Propriétés** , une zone de description affiche des informations relatives au champ de propriété sélectionné. Cette fonctionnalité est activée par défaut. Si vous voulez masquer le champ de description, cliquez avec le bouton droit sur la fenêtre **Propriétés** et cliquez sur **Description**. Cette action supprime également la coche à côté du titre **Description** dans la fenêtre de menu. Vous pouvez afficher le champ à nouveau en suivant la même procédure pour réactiver **Description** .  
  
 Les informations dans le champ de description proviennent <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Chaque méthode, interface, coclasse, etc. peut avoir un attribut `helpstring` non localisé dans la bibliothèque de types. Le **propriétés** fenêtre récupère la chaîne à partir de <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Pour spécifier des chaînes d’aide localisées  
  
1.  Ajoutez l’attribut `helpstringdll` à l’instruction library dans la bibliothèque de types (`typelib`).  
  
    > [!NOTE]
    >  Cette étape est facultative si la bibliothèque de types se trouve dans un fichier de bibliothèque d’objets (.olb).  
  
2.  Spécifiez des attributs `helpstringcontext` pour les chaînes. Vous pouvez également spécifier des attributs `helpstring` .  
  
     Ces attributs sont distincts des attributs `helpfile` et `helpcontext` qui sont contenus dans les vraies rubriques d’aide du fichier .chm.  
  
 Pour récupérer les informations de description à afficher pour le nom de la propriété mise en surbrillance, le **propriétés** fenêtre appels <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> pour la propriété est sélectionnée, en spécifiant le texte souhaité `lcid` d’attribut pour le chaîne de sortie. En interne, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> recherche le fichier .dll spécifié dans le `helpstringdll` attribut et les appels `DLLGetDocumentation` sur le fichier .dll avec le contexte spécifié et `lcid` attribut.  
  
 La signature et l’implémentation de `DLLGetDocumentation` sont les suivantes :  
  
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
  
 En interne, un fichier .olb est créé, qui est effectivement une DLL. Cette DLL contient une ressource, le fichier de bibliothèque de types (.tlb) et une fonction exportée, `DLLGetDocumentation`.  
  
 Dans le cas des fichiers .olb, l’attribut `helpstringdll` est facultatif, car il s’agit du même fichier qui contient le fichier .tlb lui-même.  
  
 Par conséquent, pour que des chaînes s’affichent dans le volet **Descriptions** , vous devez au moins spécifier l’attribut `helpstring` dans la bibliothèque de types. Si vous voulez que ces chaînes soient localisées, vous devez spécifier l’attribut `helpstringdll` (facultatif) et l’attribut `helpstringcontext` (obligatoire), et implémenter `DLLGetDocumentation`.  
  
 Aucune autre interface ne doit être implémentée lors de la localisation d’informations par le biais de l’attribut `helpstringcontext` d’idl et `DLLGetDocumentation`.  
  
 Une autre façon d’obtenir le nom localisé et la description d’une propriété est en implémentant <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Pour plus d’informations sur l’implémentation de cette méthode, consultez [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Interfaces et les champs de la fenêtre Propriétés](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Étendre les propriétés](../extensibility/internals/extending-properties.md)   
 [helpstringdll](http://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString](http://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](http://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [HelpContext](http://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](http://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](http://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)