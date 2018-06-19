---
title: À l’aide du modèle Automation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 679e9966e66de1c79cb3c6394f1d80ab6d6733bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31136534"
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