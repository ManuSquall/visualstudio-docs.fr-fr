---
title: "À l’aide du modèle Automation | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 82a9c2068bdd3e234bcc53ffa870ca289289d690
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="using-the-automation-model"></a>À l’aide du modèle Automation
Après vous être connecté à votre VSPackage à l’automation, vous pouvez obtenir les propriétés et méthodes en appelant le <xref:EnvDTE.DTEClass.GetObject%2A> méthode sur le <xref:EnvDTE._DTE> objet, en passant une chaîne qui représente l’objet que vous souhaitez récupérer.  
  
## <a name="obtaining-project-objects"></a>Obtention d’objets du projet  
 Voici deux exemples de code qui montrent comment un client automation Obtient le projet objets automation. Pour plus d’informations sur l’obtention de l’objet DTE, consultez [Comment : obtenir des références pour les objets DTE et DTE2](http://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp  
void DoAutomation(void)  
{  
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.  
    pMyPkg = pDTE->GetObject("AcmeProjects");   
  
   // The '=' performs a Query Interface.  
   // Assumes pDTE is already available as a global.  
   // Use pMyPkg to access your projects object's properties and methods.  
}  
  
```  
  
 À ce stade, vous pouvez utiliser les objets de projet standard qui font partie d’un VSPackage spécifique pour descendre le modèle de hiérarchie.  
  
 L’exemple de code suivant montre comment obtenir un objet personnalisé qui est une propriété d’un type de projet personnalisé. :  
  
```vb  
Dim MyPrj As Project  
Dim MyPrjItem As ProjectItem  
Dim objMyObject as MyExtendedObject  
  
MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project  
objMyObject = MyPrj.Object 'You call .Object to get to special Project  
                           'implementation  
objMyObject.MySpecialMethodOrProperty  
```  
  
 Le code suivant répertorie les noms de toutes les propriétés dans le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] environnement **général** option sur le **outils** menu :  
  
```vb  
dim objDTE  
dim objEnv  
set objDTE = CreateObject("VisualStudio.DTE")  
set objEnv = objDTE.Properties("Environment", "General")  
for each obj in ObjEnv  
MsgBox obj.Name  
Next  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:EnvDTE.DTEClass.GetObject%2A>
