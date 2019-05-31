---
title: À l’aide du modèle Automation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be793e5cc4db30fa410e0218a7f780b6c2826838
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324599"
---
# <a name="using-the-automation-model"></a>Utilisation du modèle d’automatisation
Une fois que vous avez connecté votre VSPackage à automation, vous pouvez obtenir les propriétés et méthodes en appelant le <xref:EnvDTE.DTEClass.GetObject%2A> méthode sur le <xref:EnvDTE._DTE> objet, en passant une chaîne qui représente l’objet que vous souhaitez récupérer.

## <a name="obtaining-project-objects"></a>Obtention d’objets du projet
 Voici deux exemples de code qui montrent la façon dont un utilisateur d’automation Obtient le projet objets automation. Pour plus d’informations sur l’obtention de l’objet DTE, consultez [Comment : Obtenir des références pour les objets DTE et DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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
- <xref:EnvDTE.DTEClass.GetObject%2A>