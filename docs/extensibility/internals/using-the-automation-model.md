---
title: Utilisation du modèle d’automatisation (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d7bd789a41f7a5e801552ca07f9f228921867
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704217"
---
# <a name="using-the-automation-model"></a>Utilisation du modèle d’automatisation
Une fois que vous avez connecté votre VSPackage à l’automatisation, vous pouvez obtenir les propriétés et les méthodes en appelant la <xref:EnvDTE.DTEClass.GetObject%2A> méthode sur l’objet, <xref:EnvDTE._DTE> en passant une chaîne représentant l’objet que vous souhaitez récupérer.

## <a name="obtaining-project-objects"></a>Obtenir des objets de projet
 Voici deux exemples de code qui montrent comment un consommateur d’automatisation obtient les objets d’automatisation du projet. Pour plus d’informations sur la façon d’obtenir l’objet DTE, voir [Comment: Obtenir des références aux objets DTE et DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

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

 L’exemple de code suivant montre comment obtenir un objet personnalisé qui est une propriété d’un type de projet personnalisé.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 Le code suivant répertorie les [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] noms de toutes les propriétés de l’option **environnement général** sur le menu **Outils** :

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
