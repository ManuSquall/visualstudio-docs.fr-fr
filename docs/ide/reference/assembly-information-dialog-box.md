---
title: Informations de l’assembly (boîte de dialogue)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 411a9b1150961307a2a8ed3cdfae9842fb56701c
ms.sourcegitcommit: 13decf878b33fc0c5d665a88067170c2861b261b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71681619"
---
# <a name="assembly-information-dialog-box"></a>Informations de l’assembly, boîte de dialogue

La boîte de dialogue Informations de l’assembly permet de spécifier les valeurs des attributs d’assembly globaux du .NET Framework, lesquels sont stockés dans le fichier AssemblyInfo créé automatiquement avec votre projet. Dans l’Explorateur de solutions, le fichier AssemblyInfo se trouve dans le nœud **Mon projet** pour les projets Visual Basic (cliquez sur **Afficher tous les fichiers** pour l’afficher). Pour les projets C#, il se trouve sous **Propriétés**. Pour plus d’informations, consultez [Attributs (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans **l’Explorateur de solutions**, puis, dans le menu **Projet**, sélectionnez **Propriétés**. Sur la page **Application**, sélectionnez le bouton **Informations de l’assembly**.

## <a name="uielement-list"></a>Liste UIElement

**Titre**\
Spécifie un titre pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTitleAttribute>.

**Description**\
Spécifie une description facultative pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Company**\
Spécifie un nom de société pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCompanyAttribute>.

Vous pouvez définir ou modifier la valeur par défaut pour Company dans le registre. Recherchez la valeur **RegisteredOrganization** sous la clé **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** ou **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion**, selon votre version de Windows.

**Product**\
Spécifie un nom de produit pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyProductAttribute>.

**Copyright**\
Spécifie une mention de droits d’auteur pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Trademark**\
Spécifie une marque pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Assembly Version**\
Spécifie la version de l’assembly. Correspond à <xref:System.Reflection.AssemblyVersionAttribute>.

**File Version**\
Spécifie un numéro de version qui indique au compilateur d’utiliser une version spécifique pour la ressource de la version du fichier Win32. Correspond à <xref:System.Reflection.AssemblyFileVersionAttribute>.

**GUID**\
GUID unique qui identifie l’assembly. Quand vous créez un projet, Visual Studio génère un GUID pour l’assembly. Correspond à <xref:System.Guid>.

**Neutral Language**\
Spécifie la culture prise en charge par l'assembly. Correspond à <xref:System.Resources.NeutralResourcesLanguageAttribute>. La valeur par défaut est **(Aucun)** .

**Make assembly COM-Visible**\
Spécifie si les types dans l’assembly seront disponibles pour COM. Correspond à <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Pour plus d’informations sur la définition de ces propriétés lors de la génération d’un package NuGet dans une bibliothèque de classes .NET Framework, consultez [configurer les propriétés du projet pour le package](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Voir aussi

- [Page Application, Concepteur de projets (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Attributs](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
