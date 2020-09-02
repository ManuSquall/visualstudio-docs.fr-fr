---
title: Méthode Setwefprocessid,
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537330"
---
# <a name="setwefprocessid-method"></a>Méthode Setwefprocessid,
  Fournit l’identificateur de processus qui exécutera le contenu WEF (Web extensions Framework).

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*dwProcessId*|Identificateur de processus qui sera utilisé pour exécuter le contenu WEF.|

## <a name="return-value"></a>Valeur retournée
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Notes
 Cette méthode doit être appelée après la création du processus de contenu WEF, mais avant l’exécution de tout contenu WEF.

 Si vous souhaitez que l’environnement de développement attache un débogueur au processus de contenu WEF, l’environnement doit effectuer cette opération dans votre implémentation de cette méthode.
