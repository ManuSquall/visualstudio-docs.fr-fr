---
title: Interface Iwefdebuggingsupport,
description: Découvrez comment vous pouvez utiliser un environnement de débogage tel que Visual Studio pour faciliter le débogage des applications Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9fc319429414c8976d748a30ecdd1e164ce22b63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962260"
---
# <a name="iwefdebuggingsupport-interface"></a>Interface Iwefdebuggingsupport,
  Implémenté par un environnement de débogage, tel que Visual Studio, pour faciliter le débogage des applications pour Office. L’application Office, telle que Word ou Excel, obtient cette interface à partir de Visual Studio, puis appelle les méthodes sur l’interface à certains points pendant la session de débogage.

## <a name="syntax"></a>Syntaxe

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Méthodes
 Le tableau suivant répertorie les méthodes définies par l’interface Iwefdebuggingsupport,.

|Nom|Description|
|----------|-----------------|
|[Méthode Getautoinsertextensions,](../vsto/getautoinsertextensions-method.md)|Obtient des informations sur les applications pour Office qui doivent être insérées automatiquement pendant le débogage.|
|[Méthode Setwefprocessid,](../vsto/setwefprocessid-method.md)|Fournit l’identificateur de processus qui exécutera le contenu WEF (Web extensions Framework).|
