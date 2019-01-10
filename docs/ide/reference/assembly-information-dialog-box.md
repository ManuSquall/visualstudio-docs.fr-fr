---
title: Informations de l’assembly (boîte de dialogue)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1145c1369f13c04957b4b0f4c4ccf84569773986
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882985"
---
# <a name="assembly-information-dialog-box"></a>Informations de l’assembly (boîte de dialogue)
La boîte de dialogue **Informations de l’assembly** permet de spécifier les valeurs des attributs d’assembly globaux [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)], lesquels sont stockés dans le fichier AssemblyInfo créé automatiquement avec votre projet. Dans l’**Explorateur de solutions**, le fichier se trouve dans le nœud **Mon projet** dans [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] (cliquez sur **Afficher tous les fichiers** pour l’afficher) ; il se trouve sous **Propriétés** dans [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]. Pour plus d’informations sur les attributs d’assembly, consultez [Attributs](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis dans le menu **Projet**, cliquez sur **Propriétés**. Quand le **Concepteur de projet** s’affiche, cliquez sur l’onglet **Application**. Dans la page **Application**, cliquez sur le bouton **Informations de l’assembly**.

## <a name="uielement-list"></a>Liste des éléments d’interface
 **Titre** Spécifie un titre pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTitleAttribute>.

 **Description** Spécifie une description facultative pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Société** Spécifie un nom de société pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Produit** Spécifie un nom de produit pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyProductAttribute>.

 **Copyright** Spécifie une mention de droits d’auteur pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Marque** Spécifie une marque pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Version de l’assembly** Spécifie la version de l’assembly. Correspond à <xref:System.Reflection.AssemblyVersionAttribute>.

 **Version de fichier** Spécifie un numéro de version qui indique au compilateur d’utiliser une version spécifique pour la ressource de la version du fichier Win32. Correspond à <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **GUID** GUID unique qui identifie l’assembly. Quand vous créez un projet, Visual Studio génère un GUID pour l’assembly. Correspond à <xref:System.Guid>.

 **Indépendant de la langue** Spécifie la culture prise en charge par l’assembly. Correspond à <xref:System.Resources.NeutralResourcesLanguageAttribute>. La valeur par défaut est **(Aucun)**.

 **Rendre l’assembly visible par COM** Spécifie si les types dans l’assembly seront disponibles pour COM. Correspond à <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>Voir aussi

- [Page Application, Concepteur de projets (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)
- [Attributs](https://msdn.microsoft.com/Library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)