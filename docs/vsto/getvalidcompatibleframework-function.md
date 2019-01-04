---
title: Getvalidcompatibleframework, fonction
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30a116993535e3b99b4e91edf07752c00a020859
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835485"
---
# <a name="getvalidcompatibleframework-function"></a>Getvalidcompatibleframework, fonction
  Cette API prend en charge l’infrastructure Office et n’est pas destinée à être utilisée directement à partir de votre code.  

## <a name="syntax"></a>Syntaxe  

```csharp 
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  

### <a name="parameters"></a>Paramètres  

|Paramètre|Description|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|N’utilisez pas.|  
|*pbstrValidFrameworkTag*|N’utilisez pas.|  

## <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, elle retourne **S_OK**. Si la fonction échoue, elle retourne un code d’erreur.  
