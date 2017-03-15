---
title: "IDebugClassField::GetDefaultIndexer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetDefaultIndexer"
helpviewer_keywords: 
  - "IDebugClassField::GetDefaultIndexer (méthode)"
ms.assetid: 47ce4f45-3816-4b40-909c-5032d0692d75
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugClassField::GetDefaultIndexer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le nom de l'indexeur par défaut.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetDefaultIndexer(   
   BSTR* pbstrIndexer  
);  
```  
  
```c#  
int GetDefaultIndexer(  
   out string pbstrIndexer  
);  
```  
  
#### Paramètres  
 `pbstrIndexer`  
 \[out\]  Retourne une chaîne contenant le nom de l'indexeur par défaut.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a aucun indexeur par défaut.  Sinon, retourne un code d'erreur.  
  
## Notes  
 L'indexeur par défaut d'une classe est la propriété qui est marquée comme propriété d' `Default` pour les accès de tableau.  c'est spécifique à [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  Voici un exemple d'un indexeur par défaut déclaré dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] et son utilisation.  
  
```vb#  
Imports System.Collections;  
  
Public Class Class1  
    Private myList as Hashtable  
  
    Default Public Property Item(ByVal Index As Integer) As Integer  
        Get  
            Return CType(List(Index), Integer)  
        End Get  
        Set(ByVal Value As Integer)  
            List(Index) = Value  
        End Set  
    End Property  
End Class  
  
Function GetItem(Index as Integer) as Integer  
    Dim classList as Class1 = new Class1  
    Dim value as Integer  
  
    ' Access array through default indexer  
    value = classList(2)  
  
    ' Access array through explicit property  
    value = classList.Item(2)  
  
    Return value  
End Function  
```  
  
## Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)