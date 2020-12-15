---
title: Utilisation du modèle Automation | Microsoft Docs
description: Découvrez comment obtenir les propriétés et les méthodes de votre VSPackage après qu’il est connecté au modèle Automation.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: ad8c02f846a946933ac07d4aa546ad3ce3a2a82f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488165"
---
# <a name="using-the-automation-model"></a>Utilisation du modèle d’automatisation
Une fois que vous avez connecté votre VSPackage à Automation, vous pouvez obtenir les propriétés et les méthodes en appelant la <xref:EnvDTE.DTEClass.GetObject%2A> méthode sur l' <xref:EnvDTE._DTE> objet, en passant une chaîne représentant l’objet que vous souhaitez récupérer.

## <a name="obtaining-project-objects"></a>Obtention d’objets de projet
 Voici deux exemples de code qui montrent comment un consommateur Automation obtient les objets Automation de projet. Pour plus d’informations sur l’obtention de l’objet DTE, consultez [Comment : obtenir des références aux objets DTE et DTE2](/previous-versions/68shb4dw(v=vs.140)).

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

 À ce stade, vous pouvez utiliser les objets de projet standard qui font partie d’un VSPackage spécifique pour descendre dans le modèle de hiérarchie.

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

 Le code suivant répertorie les noms de toutes les propriétés de l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] option environnement **général** du menu **Outils** :

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