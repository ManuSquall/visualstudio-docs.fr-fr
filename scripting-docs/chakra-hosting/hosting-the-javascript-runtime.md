---
title: "Hébergement du JavaScript Runtime | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 30ec744e-57cc-4ef5-8fe1-d2c27b946548
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 2bf213bf262ede7642e05c66e424b860238dc57f
ms.contentlocale: fr-fr
ms.lasthandoff: 08/11/2017

---
# <a name="hosting-the-javascript-runtime"></a>Hébergement JavaScript Runtime
Les API JavaScript Runtime (JsRT) fournissent un moyen aux applications de bureau, du Windows Store et côté serveur s'exécutant sur le système d'exploitation Windows d'ajouter des fonctionnalités de script à l'application à l'aide de Chakra, le moteur JavaScript conforme aux normes, également utilisé par Internet Explorer. Ces API sont disponibles sur Windows 10 ainsi que sur n'importe quelle version du système d'exploitation Windows doté de la version 11.0 d'Internet Explorer. Pour plus d'informations, consultez [Reference (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md). Pour plus d’informations sur l’utilisation de JsRT dans les applications du Windows Store, consultez [JsRT and the Universal Windows Platform](#Windows).  
  
> [!NOTE]
>  Cette documentation suppose une familiarité générale de travail avec le langage JavaScript.  
  
## <a name="concepts"></a>Concepts  
 Comprendre comment héberger le moteur JavaScript à l'aide des API de JsRT dépend de deux concepts clés : les runtimes et les contextes d'exécution.  
  
 Un *runtime* représente un environnement complet d'exécution JavaScript. Chaque runtime créé dispose de son propre tas isolé récupéré par le garbage collector et, par défaut, de son propre thread de compilateur juste-à-temps (JIT) et thread de garbage collector (GC). Chaque *contexte d’exécution* représente un environnement JavaScript qui dispose de son propre objet global JavaScript, distinct de tous les autres contextes d’exécution. Un runtime peut contenir plusieurs contextes d'exécution, et dans ce cas, tous les contextes d'exécution partagent le compilateur JIT et le thread GC associés au runtime.  
  
 Les runtimes représentent un seul thread d'exécution. Seul un runtime peut être actif sur un thread particulier à la fois. En outre, un runtime peut seulement être actif sur un thread à la fois. Les runtimes sont actifs sur les threads en mode location. Autrement dit, un runtime actuellement inactif sur un thread (c.-à-d. qui n’exécute pas de code JavaScript ou ne répond à aucun appel de l’hôte) peut être utilisé sur tout thread sans runtime actif.  
  
 Les contextes d'exécution sont attachés à un runtime particulier et exécutent le code dans ce runtime. Contrairement aux runtimes, plusieurs contextes d'exécution peuvent être actifs sur un thread en même temps. Ainsi un hôte peut passer un appel dans un contexte d'exécution, ce contexte d'exécution peut rappeler l'hôte, et l'hôte peut passer un appel dans un contexte d'exécution différent.  
  
 ![Contextes d’exécution multiples](../chakra-hosting/media/js-chakra-hosting.png "JS_Chakra_Hosting")  
  
 En pratique, à moins qu’un hôte ne doive exécuter un code dans des environnements séparés, un seul contexte d’exécution peut être utilisé. De même, à moins qu'un hôte ne doive exécuter plusieurs segments de code simultanément, un seul runtime est suffisant.  
  
## <a name="memory-management"></a>Gestion de la mémoire  
 JavaScript est un langage avec garbage collector ; il convient donc de tenir compte de plusieurs considérations lorsque vous travaillez avec les API de JsRT depuis un autre langage.  
  
 La principale considération étant que le garbage collector de JavaScript ne peut voir que des références à des valeurs à deux emplacements : le tas de son runtime et la pile. Ainsi, une référence à une valeur JavaScript stockée dans une autre valeur JavaScript ou dans une variable locale sur la pile sera toujours vue par le garbage collector. Mais des références stockées dans d'autres emplacements, tels que les tas managés par l'hôte ou le système, ne sont pas visibles par le garbage collector et peuvent entraîner la collection prématurée de valeurs qui sont encore utilisées par l'hôte.  
  
> [!IMPORTANT]
>  Certains compilateurs de langage (tels que le compilateur Visual Studio C++) optimiseront vos variables locales lorsque cela est possible. Veillez à ce que les variables locales qui référencent des valeurs JavaScript sont sur la pile si elles sont censées conserver ces valeurs actives.  
  
 Si une référence à une valeur JavaScript est stockée dans un emplacement non visible par le garbage collector, l'hôte doit ajouter et supprimer manuellement les références à l'aide des API de JsRT.  
  
## <a name="exception-handling"></a>Gestion des exceptions  
 Lorsqu'une exception JavaScript se produit pendant l'exécution du script, le runtime en question est mis dans un état d'exception. Dans un état d'exception, aucun code ne peut s'exécuter et tous les appels de l'API échoueront avec le code d'erreur `JsErrorInExceptionState` jusqu'à ce que l'hôte récupère et désactive l'exception à l'aide de l'API `JsGetAndClearException` . Si l'hôte renvoie un résultat après un rappel JavaScript sans retirer l'état d'exception du runtime, l'exception JavaScript sera renvoyée à nouveau dès que le contrôle repasse au moteur JavaScript. Cela permet également aux rappels de l’hôte de « lever » une exception JavaScript en mettant le runtime dans un état d’exception, puis en retournant un résultat après un rappel de l’hôte.  
  
 Un hôte n'est pas autorisé à laisser ses propres exceptions internes se propager dans un rappel d'hôte ; les méthodes de rappel doivent intercepter toutes les exceptions provenant d'un hôte avant de renvoyer le contrôle au runtime.  
  
## <a name="runtime-resource-usage"></a>Utilisation des ressources d'exécution  
 Les API de JsRT exposent plusieurs façons de surveiller et de modifier la façon dont les runtimes utilisent les ressources. Elles se répartissent généralement comme suit :  
  
-   **Utilisation des threads**. Par défaut, chaque runtime créera un thread compilateur JIT dédié et un thread GC dédié qui desservent ce runtime. Si un runtime est créé avec l'indicateur `JsRuntimeAttributeDisableBackgroundWork` , le travail JIT et du GC sera exécuté sur le thread d'exécution lui-même et non sur leurs threads distincts respectifs en arrière-plan. Un hôte peut également fournir un rappel de service de thread à l'appel `JsCreateRuntime` , ce qui permettra à l'hôte de planifier le travail JIT et du GC qui lui convient.  
  
-   **Utilisation de la mémoire**. Il existe plusieurs façons de contrôler et de modifier l'utilisation de la mémoire d'un runtime. Si le runtime a une exécution prolongée, l'hôte peut spécifier l'indicateur `JsRuntimeAttributeEnableIdleProcessing` lorsqu'il crée le runtime, puis appeler `JsIdle` lorsque l'hôte est dans un état inactif. Cela permet au moteur de différer un travail de nettoyage et de comptabilité de mémoire jusqu'à l'état d'inactivité.  
  
     L'hôte peut surveiller les processus de garbage collection en appelant `JsSetRuntimeBeforeCollectCallback`. Il peut surveiller également des allocations effectuées par le tas en appelant `JsSetRuntimeMemoryAllocationCallback`. Notez que cette API ne fait pas de rappel sur chaque allocation JavaScript, mais seulement au moment où le tas du runtime a besoin de plus d’espace à allouer. Le rappel d'allocation de mémoire est autorisé à refuser la demande, ce qui déclenchera un processus de garbage collection et, si aucune mémoire n'est disponible, une erreur de mémoire insuffisante pour le runtime.  
  
     L'hôte peut également appeler `JsSetRuntimeMemoryLimit` pour définir une limite pour la quantité de mémoire qu'un runtime peut utiliser. Lorsqu'un runtime atteint une limite, cela déclenche un processus de garbage collection et, si aucune mémoire n'est disponible, une erreur de mémoire insuffisante sera renvoyée par le runtime.  
  
-   **Interruption et évaluation du script**. L'hôte peut appeler `JsDisableRuntimeExecution` pour arrêter une exécution dans un runtime. Cet appel peut être fait à tout moment et dans n'importe quel thread. Comme l'arrêt de script est conditionné par l'atteinte de points de garde insérés dans le code, un script peut ne pas se terminer au moment exact, mais le fera rapidement après. Par défaut, des points de garde d'arrêt sont placés dans le code généré de façon conventionnelle et peuvent ne pas couvrir chaque situation, comme une boucle infinie par exemple. La création du runtime avec l'indicateur `JsRuntimeAttributeAllowScriptInterrupt` provoque une insertion par le runtime de contrôles additionnels pour les boucles infinies, souvent au prix d'une petite surcharge de performances.  
  
     Si un hôte souhaite interdire la génération de code natif par le compilateur JIT, il peut spécifier l'indicateur `JsRuntimeAttributeDisableNativeCodeGeneration` . Un hôte peut également interdire aux scripts de s'exécuter dynamiquement en spécifiant l'indicateur `JsRuntimeAttributeDisableEval` .  
  
## <a name="debugging-and-profiling"></a>Débogage et profilage  
 Les API de JsRT prennent en charge le débogage et le profilage via la technologie Active Scripting.  
  
 À compter de Windows 10, le moteur Chakra JavaScript prend en charge un moteur hérité et un moteur Edge, et vous pouvez cibler l’un ou l’autre dans JsRT (pour plus d’informations, consultez [Ciblage du moteur Edge ou des moteurs hérités](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)). Le débogage d'un script dans Visual Studio fonctionne différemment entre les moteurs hérité et Edge. Avec le moteur hérité, l’hôte doit fournir un pointeur d’[interface IDebugApplication](../winscript/reference/idebugapplication-interface.md), qui peut être obtenu à partir d’une instance d’[interface IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md). Avec le moteur Edge, `IDebugApplication` est déconseillé et le moteur Chakra permet des fonctionnalités de débogage natif et de script via le débogueur Visual Studio, sans que l'utilisateur doive implémenter `IDebugApplication` .  
  
 Pour rendre débogable des scripts dans un contexte d'exécution, le moteur Chakra doit utiliser des méthodes d'exécution du code moins efficaces. Ainsi, le code débogable s'exécute généralement plus lentement que du code non-débogable. De ce fait, avec le moteur hérité, un hôte peut choisir de démarrer le débogage dans un contexte d'exécution dès le départ, en fournissant le pointeur `IDebugApplication` au préalable via `JsCreateContext`, ou il peut attendre d'avoir besoin du débogage, puis appeler `JsStartDebugging`. Avec le moteur Edge, `JsCreateContext` n'a plus besoin d'un paramètre `IDebugApplication` et, par conséquent, le script est débogable uniquement une fois que `JsStartDebugging` est appelé. Durant le débogage avec Visual Studio, l’option de débogueur « Script » doit être activée.  
  
 Le code JavaScript dans un contexte d'exécution peut être profilé de deux façons. Le profileur Visual Studio de ligne de commande (vsperf.exe) peut être utilisé dans Windows 8.1 et versions ultérieures avec le commutateur /js pour produire un rapport qui cible l'exécution du code JavaScript dans l'application. Ou l'hôte peut appeler directement `JsStartProfiling` et `JsStopProfiling` et fournir un rappel pour faire le profilage lui-même. L'hôte peut également examiner l'état du tas récupéré par le garbage collector en appelant `JsEnumerateHeap`. Le profilage fonctionne dans JsRT de la même façon entre les moteurs hérité et Edge. Toutefois, les API de profilage JsRT (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`et `JsIsEnumeratingHeap`) ne sont pas disponibles pour les applications Windows universelles.  
  
<a name="Windows"></a>   
## <a name="jsrt-and-the-universal-windows-platform"></a>JsRT and the Universal Windows Platform  
 Vous pouvez utiliser les API JsRT pour ajouter des fonctionnalités de script à une application Windows universelle. Une application Windows universelle qui utilise les API JsRT doit cibler les API JSRT Edge, qui à leur tour ciblent le moteur Chakra Edge. Pour plus d'informations, consultez [Ciblage du moteur Edge vs. des moteurs hérités](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md). L'API JsRT complète est disponible pour les applications Windows universelles, à l'exception de la prise en charge du profilage et de l'énumération de tas (`JsStartProfiling`, `JsStopProfiling`, `JsEnumerateHeap`et `JsIsEnumeratingHeap` ne sont pas pris en charge).  
  
 JsRT permet également aux scripts d’accéder en mode natif aux [API de la plateforme Windows universelle (UWP, Universal Windows Platform)](https://msdn.microsoft.com/en-us/library/windows/apps/br211377.aspx) après l’exposition de l’espace de noms API via l’API JsRT Edge `JsProjectWinRTNamespace`. Bien que les applications Windows universelles ne requièrent aucune configuration autre que la projection des espaces de noms nécessaires, dans une Application Windows standard (Win32), un mécanisme de pompage délégué initialisé par COM doit être activé via `JsSetProjectionEnqueueCallback` pour permettre les événements et les API asynchrones. L'exemple Win32 suivant utilise des API UWP asynchrones pour créer un client http afin d'obtenir du contenu à partir d'un Uri :  
  
```cpp  
typedef struct _jsCall {  
    JsProjectionCallback jsCallback;  
    JsProjectionCallbackContext jsContext;  
    HANDLE event;  
} jsCall;  
  
// Set up delegated pumping mechanism; not necessary in UWP applications.  
jsCall outstandingCall = {};  
CoInitializeEx(nullptr, COINIT_MULTITHREADED);  
JsSetProjectionEnqueueCallback([](JsProjectionCallback jsCallback,   
JsProjectionCallbackContext jsContext, void *callbackState) {  
    jsCall* call = (jsCall*)callbackState;  
    call->jsCallback = jsCallback;  
    call->jsContext = jsContext;  
    SetEvent(call->event);  
    },  
&outstandingCall);  
HANDLE event = CreateEventEx(NULL, NULL, CREATE_EVENT_MANUAL_RESET, EVENT_ALL_ACCESS);  
outstandingCall.event = event;  
  
// Project necessary namespaces.  
JsProjectWinRTNamespace(L"Windows.Foundation");  
JsProjectWinRTNamespace(L"Windows.Web");  
  
// Get content from an Uri.  
JsRunScript(L"var uri = new Windows.Foundation.Uri(\"http://somedatasource.com\"); " \  
    L"var httpClient = new Windows.Web.Http.HttpClient();" \  
    L"httpClient.getStringAsync(uri).done(function (content) { " \  
    L"    // do something with the string content " \    
    L"}, onError); " \  
    L"function onError(reason) { " \  
    L"    // error handling " \        
    L"}",   
    currentSourceContext, L"", &result);  
  
// Wait for async call to come in and then execute; not necessary in UWP applications.  
WaitForSingleObjectEx(outstandingCall.event, 10000, FALSE) == WAIT_OBJECT_0;  
outstandingCall.jsCallback(outstandingCall.jsContext);  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple d’application JavaScript Runtime](http://go.microsoft.com/fwlink/p/?LinkID=306674&clcid=0x409)   
 [Référence (JavaScript Runtime)](../chakra-hosting/reference-javascript-runtime.md)   
 [Hébergement JavaScript Runtime](../chakra-hosting/javascript-runtime-hosting.md)
