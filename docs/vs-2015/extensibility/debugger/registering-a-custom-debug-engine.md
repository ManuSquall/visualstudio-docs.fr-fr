---
title: Inscription d’un moteur de débogage personnalisé | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, registering
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9cf06e881034b980b8e40e095779007b3c7fa6f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703604"
---
# <a name="registering-a-custom-debug-engine"></a>Inscription d’un moteur de débogage personnalisé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le moteur de débogage doit s’inscrire en tant que fabrique de classe en suivant les conventions COM et s’inscrire auprès de Visual Studio via la sous-clé de Registre Visual Studio.  
  
> [!NOTE]
> Vous trouverez un exemple de la procédure d’inscription d’un moteur de débogage dans l’exemple TextInterpreter, qui est généré dans le cadre du [Didacticiel : génération d’un moteur de débogage à l’aide d’ATL com](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processus serveur DLL  
 En règle générale, un moteur de débogage est implémenté dans sa propre DLL en tant que serveur COM. Cela signifie que le moteur de débogage doit inscrire le CLSID de sa fabrique de classe avec COM avant que Visual Studio puisse y accéder. Ensuite, le moteur de débogage doit s’inscrire auprès de Visual Studio lui-même afin d’établir toutes les propriétés (également appelées métriques) prises en charge par le moteur de débogage. Le choix des métriques écrites dans la sous-clé de Registre Visual Studio pour le moteur de débogage dépend des fonctionnalités prises en charge par le moteur de débogage.  
  
 Les [applications auxiliaires du SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) décrivent non seulement les emplacements de Registre nécessaires à l’inscription d’un moteur de débogage. elle décrit également la bibliothèque dbgmetric. lib, qui contient un certain nombre de déclarations et de fonctions utiles pour les développeurs C++ qui facilitent la manipulation du Registre.  
  
### <a name="example"></a>Exemple  
 Voici un exemple typique (à partir de l’exemple TextInterpreter) qui montre comment utiliser la `SetMetric` fonction (à partir de dbgmetric. lib) pour inscrire un moteur de débogage avec Visual Studio. Les métriques transmises sont également définies dans dbgmetric. lib.  
  
> [!NOTE]
> TextInterpreter est un moteur de débogage de base ; elle n’implémente pas, et par conséquent, n’enregistre pas les autres fonctionnalités. Un moteur de débogage plus complet contient une liste complète d' `SetMetric` appels ou leur équivalent, un pour chaque fonctionnalité prise en charge par le moteur de débogage.  
  
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
 [Applications auxiliaires du kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Didacticiel : création d’un moteur de débogage à l’aide d’ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
