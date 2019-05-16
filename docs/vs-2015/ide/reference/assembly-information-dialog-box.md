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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbcc8f31d00c270cf0eb9af8d3283a8674a639e3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703706"
---
# <a name="assembly-information-dialog-box"></a>Informations de l’assembly, boîte de dialogue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La boîte de dialogue **Informations de l’assembly** permet de spécifier les valeurs des attributs d’assembly globaux [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], lesquels sont stockés dans le fichier AssemblyInfo créé automatiquement avec votre projet. Dans l’**Explorateur de solutions**, le fichier se trouve dans le nœud **Mon projet** dans [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] (cliquez sur **Afficher tous les fichiers** pour l’afficher) ; il se trouve sous **Propriétés** dans [!INCLUDE[csprcs](../../includes/csprcs-md.md)]. Pour plus d’informations sur les attributs d’assembly, consultez [Attributs](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205).  
  
 Pour accéder à cette boîte de dialogue, sélectionnez un nœud de projet dans l’**Explorateur de solutions**, puis dans le menu **Projet**, cliquez sur **Propriétés**. Quand le **Concepteur de projet** s’affiche, cliquez sur l’onglet **Application**. Dans la page **Application**, cliquez sur le bouton **Informations de l’assembly**.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 **Titre**  
 Spécifie un titre pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTitleAttribute>.  
  
 **Description**  
 Spécifie une description facultative pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyDescriptionAttribute>.  
  
 **Société**  
 Spécifie un nom de société pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCompanyAttribute>.  
  
 **Produit**  
 Spécifie un nom de produit pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyProductAttribute>.  
  
 **Copyright**  
 Spécifie une mention de droits d’auteur pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyCopyrightAttribute>.  
  
 **Marque**  
 Spécifie une marque pour le manifeste de l’assembly. Correspond à <xref:System.Reflection.AssemblyTrademarkAttribute>.  
  
 **Version de l’assembly**  
 Spécifie la version de l’assembly. Correspond à <xref:System.Reflection.AssemblyVersionAttribute>.  
  
 **Version de fichier**  
 Spécifie un numéro de version qui indique au compilateur d’utiliser une version spécifique pour la ressource de la version du fichier Win32. Correspond à <xref:System.Reflection.AssemblyFileVersionAttribute>.  
  
 **GUID**  
 GUID unique qui identifie l’assembly. Quand vous créez un projet, Visual Studio génère un GUID pour l’assembly. Correspond à <xref:System.Guid>.  
  
 **Langage neutre**  
 Spécifie la culture prise en charge par l'assembly. Correspond à <xref:System.Resources.NeutralResourcesLanguageAttribute>. La valeur par défaut est **(Aucun)**.  
  
 **Rendre l’assembly visible par COM**  
 Spécifie si les types dans l’assembly seront disponibles pour COM. Correspond à <xref:System.Runtime.InteropServices.ComVisibleAttribute>.  
  
## <a name="see-also"></a>Voir aussi  
 [Page Application, Concepteur de projets (Visual Basic)](../../ide/reference/application-page-project-designer-visual-basic.md)   
 [Attributs](https://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
