---
title: À l’aide du modèle Automation | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22ee836f5a4330c551181f01229e82eb14623fb8
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675207"
---
# <a name="using-the-automation-model"></a>Utilisation du modèle d’automatisation
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une fois que vous avez connecté votre VSPackage à automation, vous pouvez obtenir les propriétés et méthodes en appelant le <xref:EnvDTE.DTEClass.GetObject%2A> méthode sur le <xref:EnvDTE._DTE> objet, en passant une chaîne qui représente l’objet que vous souhaitez récupérer.  
  
## <a name="obtaining-project-objects"></a>Obtention d’objets du projet  
 Voici deux exemples de code qui montrent la façon dont un utilisateur d’automation Obtient le projet objets automation. Pour plus d’informations sur l’obtention de l’objet DTE, consultez [Comment : Obtenir des références pour les objets DTE et DTE2](https://msdn.microsoft.com/library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).  
  
```vb  
Sub DoAutomation()  
    Dim MyProjects As Projects  
    MyProjects = DTE.GetObject("AcmeProject")  
End Sub  
```  
  
```cpp#  
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
  
 Le code suivant répertorie les noms de toutes les propriétés dans le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] environnement **général** option sur le **outils** menu :  
  
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
