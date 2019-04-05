---
title: Référence de l’API (débogage de Visual Studio) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2571054e2fc90e770aec89b22c6a0b5e52786ba7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58948936"
---
# <a name="api-reference-visual-studio-debugging"></a>Informations de référence sur les API (débogage Visual Studio)
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La section de référence inclut une vue d’ensemble conceptuelle de l’API, un guide qui présente la syntaxe et l’utilisation pour tous les éléments d’API et un large éventail d’exemples de code. Toutes les références sont répertoriées par ordre alphabétique par catégorie.  
  
 Le tableau suivant présente le commun `HRESULT` valeurs retournées par les méthodes.  
  
|Nom|Description|Value|  
|----------|-----------------|-----------|  
|S_OK|Opération réussie.|0x00000000|  
|E_UNEXPECTED|Erreur inattendue.|0x8000FFFF|  
|E_NOTIMPL|Non implémenté.|0x80004001|  
|E_OUTOFMEMORY|Mémoire insuffisante pour terminer l’opération.|0x8007000E|  
|E_INVALIDARG|Un ou plusieurs arguments ne sont pas valides.|0x80070057|  
|E_NOINTERFACE|Interface non pris en charge.|0x80004002|  
|E_POINTER|Pointeur non valide.|0x80004003|  
|E_HANDLE|Handle non valide.|0x80070006|  
|E_ABORT|Opération abandonnée.|0x80004004|  
|E_FAIL|Erreur inattendue.|0x80004005|  
|E_ACCESSDENIED|Erreur accès général d'refusé.|0x80070005|  
  
> [!NOTE]
>  Quand un [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] déboguer la méthode retourne `S_OK`, il est supposé que toutes les pointeurs de paramètre sont valides, autrement dit, aucune validation n’est effectuée sur les pointeurs de paramètre lorsque `S_OK` est retourné.  
  
> [!NOTE]
>  Non valide ou `NULL` [paramètre out] peut entraîner l’IDE se bloque.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)   
 [Énumérations](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Structures et Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [Aides SDK pour le débogage](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Extensibilité du débogueur de Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
