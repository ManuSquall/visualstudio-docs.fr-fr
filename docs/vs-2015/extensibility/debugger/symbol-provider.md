---
title: Fournisseur de symboles | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178888"
---
# <a name="symbol-provider"></a>Fournisseur de symboles
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Une implémentation de l’évaluateur d’expression doit accéder aux informations de débogage symboliques générées par le compilateur de langage pour évaluer des variables et des expressions. Pour ce faire, il utilise les interfaces d’un fournisseur de symboles (SP), également appelé gestionnaire de symboles.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fournit des SPs pour le code managé, ainsi que du code natif utilisant le format de fichier de symboles de base de données du programme (PDB). À moins qu’il soit nécessaire que votre programme utilise des symboles stockés dans un format personnalisé, il est recommandé d’utiliser les SPs fournis par [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>Notes d’implémentation  
 Les [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] moteurs de débogage s’attendent à communiquer avec les SPS à l’aide d’interfaces CLR (Common Language Runtime). Par conséquent, un processeur de stockage qui fonctionne avec les moteurs de débogage Visual Studio doit prendre en charge le CLR. Une liste complète de toutes les interfaces de débogage CLR se trouve dans debugref.doc, qui fait partie de [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 Si votre SP ne fonctionne que avec votre moteur de débogage personnalisé, vous pouvez implémenter le SP comme vous le voyez en fonction des besoins de votre moteur de débogage.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants du débogueur](../../extensibility/debugger/debugger-components.md)
