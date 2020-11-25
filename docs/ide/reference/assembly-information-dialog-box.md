---
title: Informations de l’assembly (boîte de dialogue)
description: En savoir plus sur la boîte de dialogue informations de l’assembly et sur la façon dont elle est utilisée pour spécifier les valeurs des attributs d’assembly global .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee8738d06c0f02adb6f5e6352d2006e0133c66ef
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871338"
---
# <a name="assembly-information-dialog-box"></a>Informations de l’assembly (boîte de dialogue)

La boîte de dialogue Informations de l’assembly permet de spécifier les valeurs des attributs d’assembly globaux du .NET Framework, lesquels sont stockés dans le fichier AssemblyInfo créé automatiquement avec votre projet. Dans l’Explorateur de solutions, le fichier AssemblyInfo se trouve dans le nœud **Mon projet** pour les projets Visual Basic (cliquez sur **Afficher tous les fichiers** pour l’afficher). Pour les projets C#, il se trouve sous **Propriétés**. Pour plus d’informations, consultez [Attributs (C#)](/dotnet/csharp/programming-guide/concepts/attributes/index).

Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans **l’Explorateur de solutions**, puis, dans le menu **Projet**, sélectionnez **Propriétés**. Sur la page **Application**, sélectionnez le bouton **Informations de l’assembly**.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

**Bonhomme**\
Spécifie un titre pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTitleAttribute>.

**Description**\
Spécifie une description facultative pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyDescriptionAttribute>.

**Entreprise**\
Spécifie un nom de société pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCompanyAttribute>.

Vous pouvez définir ou modifier la valeur par défaut pour Company dans le registre. Recherchez la valeur **RegisteredOrganization** sous la clé **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Windows NT\CurrentVersion** ou **Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion**, selon votre version de Windows.

**Production**\
Spécifie un nom de produit pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyProductAttribute>.

**Intellectuelle**\
Spécifie une mention de droits d’auteur pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCopyrightAttribute>.

**Commerciale**\
Spécifie une marque pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTrademarkAttribute>.

**Version de l’assembly**\
Spécifie la version de l’assembly. Correspond à <xref:System.Reflection.AssemblyVersionAttribute>.

**Version du fichier**\
Spécifie un numéro de version qui indique au compilateur d’utiliser une version spécifique pour la ressource de la version du fichier Win32. Correspond à <xref:System.Reflection.AssemblyFileVersionAttribute>.

**UNIQUES**\
GUID unique qui identifie l’assembly. Quand vous créez un projet, Visual Studio génère un GUID pour l’assembly. Correspond à <xref:System.Guid>.

**Langue neutre**\
Spécifie la culture prise en charge par l'assembly. Correspond à <xref:System.Resources.NeutralResourcesLanguageAttribute>. La valeur par défaut est **(aucune)**.

**Rendre l’assembly visible par COM**\
Spécifie si les types dans l’assembly seront disponibles pour COM. Correspond à <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

> [!NOTE]
> Pour plus d’informations sur la définition de ces propriétés lors de la génération d’un package NuGet dans une bibliothèque de classes .NET Framework, consultez [configurer les propriétés du projet pour le package](/nuget/quickstart/create-and-publish-a-package-using-visual-studio-net-framework#configure-project-properties-for-the-package).

## <a name="see-also"></a>Voir aussi

- [Page Application, Concepteur de projet (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Attributs](/previous-versions/z0w1kczw(v=vs.140))