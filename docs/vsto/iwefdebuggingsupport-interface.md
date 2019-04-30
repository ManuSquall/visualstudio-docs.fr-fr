---
title: Iwefdebuggingsupport, interface
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a71adf5371275fbbdc19cdf09be96ef900ec073d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583761"
---
# <a name="iwefdebuggingsupport-interface"></a>Iwefdebuggingsupport, interface
  Implémenté par un environnement de débogage, tels que Visual Studio, afin de faciliter le débogage des applications pour Office. L’application Office, telles que Word ou Excel, obtient cette interface à partir de Visual Studio, puis appelle les méthodes sur l’interface à certains points pendant la session de débogage.

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
 Le tableau suivant répertorie les méthodes qui définit l’iwefdebuggingsupport, interface.

|Nom|Description|
|----------|-----------------|
|[Getautoinsertextensions, méthode](../vsto/getautoinsertextensions-method.md)|Obtient des informations sur les applications pour Office qui doivent être insérés automatiquement pendant le débogage.|
|[Setwefprocessid, méthode](../vsto/setwefprocessid-method.md)|Fournit l’identificateur de processus qui exécutera le contenu de l’infrastructure d’Extensions Web (WEF).|
