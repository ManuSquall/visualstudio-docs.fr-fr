---
title: 'DA0001 : Utiliser StringBuilder pour les concaténations | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da0de740155936497c2e21213d7e063fa761aade
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54804899"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001 : Utiliser StringBuilder pour les concaténations
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio 2017, consultez [DA0001 : Utilisez StringBuilder pour les concaténations](https://docs.microsoft.com/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations) sur docs.microsoft.com.  
  
|||  
|-|-|  
|ID de règle|DA0001|  
|Category|Utilisation du .NET Framework|  
|Méthodes de profilage|Échantillonnage<br /><br /> Instrumentation|  
|Message|Utilisez StringBuilder pour les concaténations de chaînes|  
|Type de message|Warning|  
  
## <a name="cause"></a>Cause  
 Les appels à System.String.Concat représentent une part importante des données de profilage. Envisagez l’utilisation de la classe <xref:System.Text.StringBuilder> pour construire des chaînes à partir de plusieurs segments.  
  
## <a name="rule-description"></a>Description de la règle  
 Un objet <xref:System.String> est immuable. Par conséquent, toute modification de la chaîne entraîne la création d’un nouvel objet String et le garbage collection de la chaîne d’origine. Ce comportement est le même si vous appelez explicitement String.Concat ou utilisez les opérateurs de concaténation de chaîne comme + ou +=. Les performances des programmes peuvent se dégrader si ces méthodes sont fréquemment appelées, par exemple lorsque des caractères sont ajoutés à une chaîne dans une boucle serrée.  
  
 La classe StringBuilder est un objet mutable, et, contrairement à System.String, la plupart des méthodes de StringBuilder qui modifient une instance de cette classe retournent une référence à cette même instance. Vous pouvez insérer des caractères ou ajouter du texte à une instance StringBuilder, et supprimer ou remplacer des caractères dans l’instance sans avoir besoin d’allouer une nouvelle instance et de supprimer l’instance d’origine.  
  
## <a name="how-to-investigate-a-warning"></a>Comment rechercher la cause d’un avertissement  
 Double-cliquez sur le message dans la fenêtre Liste d’erreurs pour accéder à la [vue Informations relatives à la fonction](../profiling/function-details-view.md) des données de profilage par échantillonnage. Recherchez les sections du programme qui utilisent le plus fréquemment la concaténation de chaînes. Utilisez la classe StringBuilder pour les manipulations de chaînes complexes, y compris les opérations fréquentes de concaténation de chaînes.  
  
 Pour plus d’informations sur l’utilisation des chaînes, consultez la section [String Operations](http://go.microsoft.com/fwlink/?LinkId=177816) de la rubrique [Chapter 5 - Improving Managed Code Performance](http://go.microsoft.com/fwlink/?LinkId=177817) dans la bibliothèque Microsoft Patterns and Practices.
