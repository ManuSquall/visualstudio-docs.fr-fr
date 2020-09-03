---
title: Informations de l’assembly, boîte de dialogue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesAssemblyInfo
helpviewer_keywords:
- Assembly Information dialog box
ms.assetid: 8f1f6449-e03d-4a5b-9076-d3b1f84ada48
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 06374f70c2552f3e635ada3bc40ef82d890fb46b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661028"
---
# <a name="assembly-information-dialog-box"></a>Informations de l’assembly (boîte de dialogue)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La boîte de dialogue **Informations de l’assembly** permet de spécifier les valeurs des attributs d’assembly globaux [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], lesquels sont stockés dans le fichier AssemblyInfo créé automatiquement avec votre projet. Dans l’**Explorateur de solutions**, le fichier se trouve dans le nœud **Mon projet** dans [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (cliquez sur **Afficher tous les fichiers** pour l’afficher) ; il se trouve sous **Propriétés** dans [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Pour plus d’informations sur les attributs d’assembly, consultez [Attributs](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).

 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis cliquez sur **Propriétés** dans le menu **Projet**. Lorsque le **Concepteur de projets** apparaît, cliquez sur l’onglet **application** . Sur la page de l' **application** , cliquez sur le bouton informations de l' **assembly** .

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur
 **Titre** Spécifie un titre pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTitleAttribute>.

 **Description** Spécifie une description facultative pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyDescriptionAttribute>.

 **Société** Spécifie un nom de société pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCompanyAttribute>.

 **Produit** Spécifie un nom de produit pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyProductAttribute>.

 **Copyright** Spécifie une mention de droits d’auteur pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCopyrightAttribute>.

 **Marque** Spécifie une marque pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTrademarkAttribute>.

 **Version de l’assembly** Spécifie la version de l’assembly. Correspond à <xref:System.Reflection.AssemblyVersionAttribute>.

 **Version de fichier** Spécifie un numéro de version qui indique au compilateur d’utiliser une version spécifique pour la ressource de la version du fichier Win32. Correspond à <xref:System.Reflection.AssemblyFileVersionAttribute>.

 **GUID** GUID unique qui identifie l’assembly. Quand vous créez un projet, Visual Studio génère un GUID pour l’assembly. Correspond à <xref:System.Guid>.

 **Indépendant de la langue** Spécifie la culture prise en charge par l’assembly. Correspond à <xref:System.Resources.NeutralResourcesLanguageAttribute>. La valeur par défaut est **(aucune)**.

 **Rendre l’assembly visible par COM** Spécifie si les types dans l’assembly seront disponibles pour COM. Correspond à <xref:System.Runtime.InteropServices.ComVisibleAttribute>.

## <a name="see-also"></a>Voir aussi
 [Page application, ](../../ide/reference/application-page-project-designer-visual-basic.md) [attributs](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205) du concepteur de projets (Visual Basic)
