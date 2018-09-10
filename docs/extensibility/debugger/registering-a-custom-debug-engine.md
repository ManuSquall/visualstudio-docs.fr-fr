---
title: Moteur de débogage de l’enregistrement personnalisé | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c87b3749c2ea63e89e2e8fb0caf773434a38df2
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281388"
---
# <a name="register-a-custom-debug-engine"></a>Inscrire un moteur de débogage personnalisé
Le moteur de débogage doit s’auto-enregistrer comme une fabrique de classe, les conventions COM suivantes mais aussi s’inscrire avec Visual Studio via la sous-clé de Registre de Visual Studio.  
  
> [!NOTE]
>  Vous trouverez un exemple montrant comment inscrire un moteur de débogage dans l’exemple TextInterpreter, qui est intégré dans le cadre de la [didacticiel : création d’un moteur de débogage à l’aide de ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processus de serveur DLL  
 Un moteur de débogage est généralement configuré dans sa propre DLL comme serveur COM. Par conséquent, le moteur de débogage doit inscrire le CLSID de la fabrique de classe avec COM avant Visual Studio peuvent y accéder. Ensuite, le moteur de débogage doit s’inscrire avec Visual Studio pour établir toutes les propriétés (autrement dit métriques) le débogage prend en charge du moteur. Le choix des métriques écrites dans la sous-clé de Registre de Visual Studio dépend des fonctionnalités que du moteur de débogage prend en charge.  
  
 [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) décrit non seulement les emplacements de Registre nécessaires pour inscrire un moteur de débogage ; il décrit également la *dbgmetric.lib* bibliothèque, qui contient un certain nombre de déclarations de fonctions utiles pour les développeurs C++ facilitant la manipulation du Registre plus facile.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant (à partir de l’exemple TextInterpreter) montre comment utiliser le `SetMetric` (fonction) (à partir de *dbgmetric.lib*) pour inscrire un moteur de débogage avec Visual Studio. Les métriques transmis sont également définies dans *dbgmetric.lib*.  
  
> [!NOTE]
>  TextInterpreter est un moteur de débogage de base ; Il n’a pas défini et par conséquent ne pas s’inscrire, d’autres fonctionnalités. Un moteur de débogage plus complète aurait une liste complète des `SetMetric` appels ou leur équivalent, pour chaque fonctionnalité, le moteur de débogage prend en charge.  
  
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
 [Création d’un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Didacticiel : Création d’un moteur de débogage à l’aide de ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)