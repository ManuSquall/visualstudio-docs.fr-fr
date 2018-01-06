---
title: "Moteur de débogage de l’enregistrement personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 50903d9b45828725da03c0fcb0db0f08d7f884eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="registering-a-custom-debug-engine"></a>L’inscription d’un moteur de débogage personnalisé
Le moteur de débogage doit s’inscrire en tant qu’une fabrique de classe suit les conventions COM ainsi enregistrer avec Visual Studio via la sous-clé de Registre de Visual Studio.  
  
> [!NOTE]
>  Vous trouverez un exemple de l’inscription d’un moteur de débogage dans l’exemple TextInterpreter, qui est intégré dans le cadre de la [didacticiel : création d’un débogage moteur à l’aide de ATL COM](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processus de serveur de DLL  
 En règle générale, un moteur de débogage est implémenté dans son propre DLL comme un serveur COM. Cela signifie que le moteur de débogage doit inscrire le CLSID de la fabrique de classe avec COM avant Visual Studio peuvent y accéder. Ensuite, le moteur de débogage doit s’inscrire dans Visual Studio afin d’établir toutes les propriétés (autrement dit métriques) le débogage prend en charge du moteur. Le choix des métriques qui sont écrits dans la sous-clé de Registre pour le moteur de débogage Visual Studio dépend des fonctionnalités que prend en charge par le moteur de débogage.  
  
 [Programmes d’assistance du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) décrit non seulement les emplacements de Registre nécessaires pour inscrire un moteur de débogage ; il décrit également la bibliothèque de dbgmetric.lib, qui contient un certain nombre de fonctions utiles pour les développeurs C++ qui rendent les déclarations manipulation du Registre plus facile.  
  
### <a name="example"></a>Exemple  
 Voici un exemple typique (à partir de l’exemple TextInterpreter) illustrant comment utiliser le `SetMetric` de fonction (à partir de dbgmetric.lib), pour inscrire un moteur de débogage avec Visual Studio. Les métriques transmises sont également définies dans dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter est un moteur de débogage de base ; Il n’implémente pas et par conséquent n’inscrit pas, toutes les autres fonctionnalités. Un moteur de débogage plus complète aurait une liste complète des `SetMetric` prend en charge les appels ou leur équivalent, un pour chaque fonctionnalité, le moteur de débogage.  
  
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
 [Programmes d’assistance du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Didacticiel : Création d’un moteur de débogage à l’aide de COM ATL](http://msdn.microsoft.com/en-us/9097b71e-1fe7-48f7-bc00-009e25940c24)