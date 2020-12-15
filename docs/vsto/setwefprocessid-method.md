---
title: Méthode Setwefprocessid,
description: Découvrez comment la méthode Setwefprocessid, fournit l’identificateur de processus qui exécute le contenu WEF (Web extensions Framework).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524321"
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
