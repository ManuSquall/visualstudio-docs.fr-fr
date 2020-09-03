---
title: Détails du runtime de contrôle de code source | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183370"
---
# <a name="source-control-runtime-details"></a>Détails du Runtime du contrôle de code source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un projet est ajouté au contrôle de code source lorsque l’utilisateur ajoute un fichier dans le projet au contrôle de code source ou via un contrôleur Automation, tel qu’un Assistant. Un projet ne spécifie pas lui-même qu’il est sous contrôle de code source ; Il prend en charge le contrôle de code source, mais doit être ajouté manuellement.  
  
## <a name="registering-with-a-source-control-package"></a>Inscription à l’aide d’un package de contrôle de code source  
 Quand un fichier de votre projet est ajouté au contrôle de code source, l’environnement appelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> pour vous fournir quatre chaînes opaques qui sont utilisées comme cookies par le système de contrôle de code source. Stockez ces chaînes dans votre fichier projet. Ces chaînes doivent être passées au stub de contrôle de code source (le composant Visual Studio qui gère les packages de contrôle de code source) au démarrage du type de projet en appelant <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . Cela charge à son tour le package de contrôle de code source approprié et transfère l’appel à son implémentation de `IVsSccManager2::RegisterSccProject` .  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [Prise en charge du contrôle de code source](../../extensibility/internals/supporting-source-control.md)
