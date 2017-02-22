---
title: "L’inscription d’un moteur de d&#233;bogage personnalis&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "moteurs de débogage, l’inscription"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# L’inscription d’un moteur de d&#233;bogage personnalis&#233;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le moteur de débogage doit s’enregistrer comme une fabrique de classe suivant conventions COM ainsi que s’inscrire avec Visual Studio via la sous\-clé de Registre Visual Studio.  
  
> [!NOTE]
>  Vous trouverez un exemple de l’enregistrement d’un moteur de débogage dans l’exemple TextInterpreter, qui est créé dans le cadre de la [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/fr-fr/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## Processus du serveur de DLL  
 En général, un moteur de débogage est implémenté dans son propre DLL comme serveur COM. Cela signifie que le moteur de débogage doit inscrire le CLSID de la fabrique de classe avec COM qu’il puisse accéder à Visual Studio. Puis le moteur de débogage doit s’inscrire dans Visual Studio afin d’établir des propriétés \(autrement dit mesures\) le débogage prend en charge du moteur. Le choix de mesures qui sont écrites dans la sous\-clé de Registre pour le moteur de débogage Visual Studio dépend des fonctionnalités que du moteur de débogage prend en charge.  
  
 [« Helpers » du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) décrit non seulement les emplacements du Registre nécessaires pour inscrire un moteur de débogage ; Il décrit également la bibliothèque dbgmetric.lib, qui contient un nombre de fonctions utiles et des déclarations pour les développeurs C\+\+ qui rendent la manipulation du Registre plus facile.  
  
### Exemple  
 Voici un exemple typique \(à partir de l’exemple TextInterpreter\), qui indique comment utiliser le `SetMetric` fonction \(à partir de dbgmetric.lib\), pour inscrire un moteur de débogage avec Visual Studio. Les mesures transmises sont également définies dans dbgmetric.lib.  
  
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
  
## Voir aussi  
 [Création d'un moteur de débogage personnalisé](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [« Helpers » du Kit de développement logiciel pour le débogage](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/fr-fr/9097b71e-1fe7-48f7-bc00-009e25940c24)