---
title: Moteur de débogage de l’enregistrement personnalisé | Microsoft Docs
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
ms.openlocfilehash: e7055d69ea387994ea8011ac779334e61b899abf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435700"
---
# <a name="registering-a-custom-debug-engine"></a>Inscription d’un moteur de débogage personnalisé
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Le moteur de débogage doit s’auto-enregistrer comme une fabrique de classe suit les conventions COM mais aussi s’inscrire avec Visual Studio via la sous-clé de Registre de Visual Studio.  
  
> [!NOTE]
> Vous trouverez un exemple montrant comment inscrire un moteur de débogage dans l’exemple TextInterpreter, qui est intégré dans le cadre de la [didacticiel : Création d’un moteur de débogage à l’aide de ATL COM](http://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## <a name="dll-server-process"></a>Processus de serveur de DLL  
 En règle générale, un moteur de débogage est implémenté dans son propre DLL comme serveur COM. Cela signifie que le moteur de débogage doit inscrire le CLSID de la fabrique de classe avec COM avant Visual Studio peuvent y accéder. Puis le moteur de débogage doit s’inscrire avec Visual Studio lui-même afin d’établir toutes les propriétés (autrement dit métriques) le débogage prend en charge du moteur. Le choix des métriques qui sont écrits dans la sous-clé de Registre de Visual Studio pour le moteur de débogage dépend des fonctionnalités que du moteur de débogage prend en charge.  
  
 [Aides SDK pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) décrit non seulement les emplacements de Registre nécessaires pour inscrire un moteur de débogage ; il décrit également la bibliothèque dbgmetric.lib, qui contient un certain nombre de fonctions utiles pour les développeurs C++ qui rendent les déclarations manipulation du Registre plus facile.  
  
### <a name="example"></a>Exemple  
 Voici un exemple typique (à partir de l’exemple TextInterpreter) montrant comment utiliser le `SetMetric` fonction (à partir de dbgmetric.lib), pour inscrire un moteur de débogage avec Visual Studio. Les métriques transmis sont également définis dans dbgmetric.lib.  
  
> [!NOTE]
> TextInterpreter est un moteur de débogage de base ; Il n’implémente pas et par conséquent ne pas s’inscrire, d’autres fonctionnalités. Un moteur de débogage plus complète aurait une liste complète des `SetMetric` appels ou leur équivalent, pour chaque fonctionnalité, le moteur de débogage prend en charge.  
  
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
 [Tutoriel : Création d’un moteur de débogage à l’aide de ATL COM](http://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)
