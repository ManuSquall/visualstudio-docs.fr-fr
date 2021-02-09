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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882406"
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

## <a name="return-value"></a>Valeur de retour
 Valeur HRESULT qui indique si la méthode a réussi.

## <a name="remarks"></a>Remarques
 Cette méthode doit être appelée après la création du processus de contenu WEF, mais avant l’exécution de tout contenu WEF.

 Si vous souhaitez que l’environnement de développement attache un débogueur au processus de contenu WEF, l’environnement doit effectuer cette opération dans votre implémentation de cette méthode.
