---
title: Enregistrement d’un moteur Debug personnalisé (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe6fb916810bc8a7e960a4723a6a7c7a6f0c1410
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713225"
---
# <a name="register-a-custom-debug-engine"></a>Enregistrer un moteur de débogé personnalisé
Le moteur de débogé doit s’inscrire comme une usine de classe, suivant les conventions COM ainsi que s’inscrire auprès de Visual Studio par le biais de la sous-clé de registre Visual Studio.

> [!NOTE]
> Vous pouvez trouver un exemple de la façon d’enregistrer un moteur de débogé dans l’échantillon TextInterpreter, qui est construit dans le cadre du [Tutorial: Building a debug moteur en utilisant ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).

## <a name="dll-server-process"></a>Processus serveur DLL
 Un moteur de débogé est généralement mis en place dans son propre DLL comme un serveur COM. En tant que tel, le moteur de débogé doit enregistrer le CLSID de son usine de classe avec COM avant Visual Studio peut y accéder. Ensuite, le moteur de débogé doit s’enregistrer auprès de Visual Studio pour établir toutes les propriétés (autrement connues sous le nom de mesures) le moteur de débogé. Le choix des mesures écrites au sous-clé du registre Visual Studio dépend des caractéristiques des supports du moteur de débogé.

 [Les aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) décrivent non seulement les emplacements de registre nécessaires pour enregistrer un moteur de déboguer; il décrit également la bibliothèque *dbgmetric.lib,* qui contient un certain nombre de fonctions et déclarations utiles pour les développeurs de CMD qui facilitent la manipulation du registre.

### <a name="example"></a>Exemple
 L’exemple suivant (à partir de l’échantillon `SetMetric` TextInterpreter) montre comment utiliser la fonction (à partir de *dbgmetric.lib*), pour enregistrer un moteur de débogé avec Visual Studio. Les mesures en cours d’adoption sont également définies en *dbgmetric.lib*.

> [!NOTE]
> TextInterpreter est un moteur de débogé de base; il ne met pas en place — et ne s’enregistre donc pas — d’autres fonctionnalités. Un moteur de débogé plus complet `SetMetric` aurait toute une liste d’appels ou leur équivalent, un pour chaque caractéristique des supports du moteur de débogé.

```
// Define base registry subkey to Visual Studio.
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";

HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)
{
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);

    return base::RegisterServer(bRegTypeLib, pCLSID);
}
```

## <a name="see-also"></a>Voir aussi
- [Création d’un moteur de débogé personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)
- [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Tutorial: Construire un moteur de débogé à l’aide d’ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)
