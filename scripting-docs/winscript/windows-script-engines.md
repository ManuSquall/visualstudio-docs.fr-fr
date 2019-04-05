---
title: Windows Script, moteurs | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows script engines
ms.assetid: e576853d-7252-4eb9-81eb-9d5bb7626ab4
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3434e9baaeb483e60087aec1b8536108c8af4471
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157761"
---
# <a name="windows-script-engines"></a>Windows Script, moteurs
Pour implémenter un moteur Microsoft Windows Script, créez un objet OLE COM qui prend en charge les interfaces suivantes.  
  
|||  
|-|-|  
|Interface|Description|  
|[IActiveScript](../winscript/reference/iactivescript.md)|Fournit les fonctionnalités de script de base. L’implémentation de cette interface est obligatoire.|  
|[IActiveScriptParse](../winscript/reference/iactivescriptparse.md)|Permet d’ajouter du texte de script, d’évaluer les expressions, etc. L’implémentation de cette interface est facultative. Toutefois, si elle n’est pas implémentée, le moteur de script doit implémenter l’une des interfaces IPersist* pour charger un script.|  
|IPersist*|Assure la prise en charge de la persistance. Vous devez implémenter au moins une des interfaces suivantes si l’interface [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) n’est pas implémentée.<br /><br /> IPersistStorage : Prend en charge l’attribut DATA={url} dans la balise OBJECT.<br /><br /> IPersistStreamInit : Prend en charge le même attribut qu’`IPersistStorage`, ainsi que l’attributDATA="string-encoded byte stream" dans la balise OBJECT.<br /><br /> IPersistPropertyBag : Prend en charge l’attribut PARAM= dans la balise OBJECT.|  
  
> [!NOTE]
>  Il est possible que le moteur de script ne soit jamais appelé pour enregistrer ou restaurer un état de script par le biais d’`IPersist*`. Au lieu de cela, l’interface [IActiveScriptParse](../winscript/reference/iactivescriptparse.md) est utilisée avec un appel à [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) pour créer un script vide, puis des scriptlets sont ajoutés et connectés à des événements avec [IActiveScriptParse::AddScriptlet](../winscript/reference/iactivescriptparse-addscriptlet.md). Enfin, du code général est ajouté avec [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Néanmoins, un moteur de script doit implémenter au moins une interface `IPersist*` (de préférence `IPersistStreamInit`), car d’autres applications hôtes peuvent tenter de les utiliser.  
  
 Les sections suivantes décrivent plus en détail l’implémentation d’un moteur de script Windows.  
  
 Pour plus d’informations, consultez [Informations de référence sur les interfaces Windows Script](../winscript/reference/windows-script-interfaces-reference.md).  
  
## <a name="registry-standard"></a>Standard de registre  
 Un moteur Windows Script peut s’identifier à l’aide d’identificateurs de catégorie. Windows Script définit actuellement deux identificateurs de catégorie.  
  
|||  
|-|-|  
|Category|Description|  
|CATID_ActiveScript|Indique que les identificateurs de classe (CLSID) sont des moteurs de Windows Script qui, au minimum, prennent en charge l’interface [IActiveScript](../winscript/reference/iactivescript.md) et un mécanisme de persistance (l’interface `IPersistStorage`, `IPersistStreamInit`, ou IPersistPropertyBag).|  
|CATID_ActiveScriptParse|Indique que les CLSID sont des moteurs Windows Script qui, au minimum, prennent en charge les interfaces [IActiveScript](../winscript/reference/iactivescript.md) et [IActiveScriptParse](../winscript/reference/iactivescriptparse.md).|  
  
 Bien qu’[IActiveScriptParse](../winscript/reference/iactivescriptparse.md) ne soit pas un véritable mécanisme de persistance, il prend en charge la méthode [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) qui équivaut du point de vue fonctionnel à `IPersist*::InitNew`.  
  
## <a name="script-engine-states"></a>États du moteur de script  
 À tout moment, un moteur Script Windows peut être dans plusieurs états.  
  
|||  
|-|-|  
|État|Description|  
|non initialisé|Le script n’a pas été initialisé ou chargé à l’aide d’une interface IPersist*, ou aucune interface [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) n’a été définie. Le moteur de script est généralement inutilisable à partir de cet état tant que le script n’est pas chargé.|  
|initialisé|Le script a été initialisé avec une interface `IPersist*` et une interface [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) est définie, mais il n’est pas connecté aux objets hôtes et aux événements de réception. Notez que cet état signifie simplement que la méthode `IPersist*::Load`, `IPersist*::InitNew`, ou [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) a été exécutée et que la méthode [IActiveScript::SetScriptSite](../winscript/reference/iactivescript-setscriptsite.md) a été appelée. Le moteur ne peut pas exécuter le code dans ce mode. Le moteur met en file d’attente le code que l’hôte lui passe par le biais de la méthode [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) et exécute le code après la transition à l’état démarré.<br /><br /> Étant donné que les langages peuvent varier énormément sur le plan sémantique, les moteurs de script ne sont pas obligés de prendre en charge cette transition d’état. Toutefois, les moteurs qui prennent en charge la méthode [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md) doivent prendre en charge cette transition d’état. Les hôtes doivent préparer cette transition et prendre les mesures appropriées : libérer le moteur de script actuel, créer un moteur de script et appeler `IPersist*::Load`, `IPersist*::InitNew` ou [IActiveScriptParse::InitNew](../winscript/reference/iactivescriptparse-initnew.md) (et éventuellement appeler [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md)). L’utilisation de cette transition doit être considérée comme une optimisation de la procédure ci-dessus. Notez que les informations que le moteur de script a obtenu sur les noms des éléments nommés et les informations de type décrivant les éléments nommés restent valides.<br /><br /> Compte tenu des différences considérables entre les langages, il est difficile de définir la sémantique exacte de cette transition. Au minimum, le moteur de script doit se déconnecter de tous les événements et libérer tous les pointeurs SCRIPTINFO_IUNKNOWN obtenus en appelant la méthode [IActiveScriptSite::GetItemInfo](../winscript/reference/iactivescriptsite-getiteminfo.md). Le moteur doit obtenir à nouveau ces pointeurs une fois que le script est réexécuté. Le moteur de script doit également réinitialiser le script à un état initial, qui est approprié pour la langue. Par exemple, VBScript réinitialise toutes les variables et conserve le code ajouté de manière dynamique en appelant [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md) avec l’indicateur SCRIPTTEXT_ISPERSISTENT défini. Les autres langages devront peut-être conserver les valeurs actuelles (comme Lisp en raison de la non-séparation du code/des données) ou revenir à un état connu (notamment les langages avec des variables initialisées de manière statique).<br /><br /> Notez que la transition à l’état démarré doit avoir la même sémantique (c’est-à-dire qu’elle doit laisser le moteur de script dans le même état) qu’un appel à `IPersist*::Save` pour enregistrer le moteur de script, suivi d’un appel à `IPersist*::Load` pour charger un nouveau moteur de script ; ces actions doivent avoir la même sémantique qu’[IActiveScript::Clone](../winscript/reference/iactivescript-clone.md). Les moteurs de script qui ne prennent pas encore en charge `IActiveScript::Clone` ou `IPersist*` doivent évaluer avec soin le comportement de la transition à l’état démarré pour qu’elle ne viole pas les conditions ci-dessus si la prise en charge d’`IActiveScript::Clone` ou d’`IPersist*` a été ajoutée par la suite.<br /><br /> Durant cette transition à l’état démarré, le moteur de script se déconnecte des récepteurs d’événements après l’exécution des destructeurs appropriés, etc. dans le script. Pour empêcher l’exécution de ces destructeurs, l’hôte peut d’abord faire passer le script à l’état déconnecté avant de le faire passer à l’état démarré.<br /><br /> Utilisez [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) pour annuler un thread de script en cours d’exécution sans attendre la fin de l’exécution des événements actuels, etc.|  
|démarré|Quand il passe de l’état initialisé à l’état démarré, le moteur exécute le code qui a été mis en file d’attente dans l’état initialisé. Le moteur peut exécuter du code dans l’état démarré, mais il n’est pas connecté aux événements ajoutés par le biais de la méthode [IActiveScript::AddNamedItem](../winscript/reference/iactivescript-addnameditem.md). Le moteur peut exécuter du code en appelant l’interface IDispatch obtenue à partir de la méthode [IActiveScript::GetScriptDispatch](../winscript/reference/iactivescript-getscriptdispatch.md) ou en appelant [IActiveScriptParse::ParseScriptText](../winscript/reference/iactivescriptparse-parsescripttext.md). Il est possible qu’une initialisation en arrière-plan (chargement progressif) soit toujours en cours et que l’appel de la méthode [IActiveScript::SetScriptState](../winscript/reference/iactivescript-setscriptstate.md) avec l’indicateur SCRIPTSTATE_CONNECTED défini provoque le blocage du script tant que l’initialisation n’est pas terminée.|  
|connecté|Le script est chargé et connecté pour la réception d’événements à partir des objets hôtes. S’il s’agit d’une transition à partir de l’état initialisé, le moteur de script doit passer par l’état démarré et effectuer les actions nécessaires avant de passer à l’état connecté et de se connecter à des événements.|  
|déconnecté|Le script est chargé dans un état d’exécution, mais la réception d’événements d’objets hôtes est temporairement déconnectée. Cela peut être effectué logiquement (en ignorant les événements reçus) ou physiquement (en appelant IConnectionPoint::Unadvise sur les points de connexion appropriés). S’il s’agit d’une transition à partir de l’état initialisé, le moteur de script doit passer par l’état démarré et effectuer les actions nécessaires avant de passer à l’état déconnecté. Les récepteurs d’événements qui sont en cours d’exécution sont terminés avant le changement de l’état (utilisez [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) pour annuler un thread de script en cours d’exécution). Cet état se distingue de l’état initialisé par les caractéristiques suivantes : la transition à cet état ne provoque pas la réinitialisation du script, l’état d’exécution du script n’est pas réinitialisée et aucune procédure d’initialisation de script n’est exécutée.|  
|fermé|Le script a été fermé. Le moteur de script ne fonctionne plus et retourne des erreurs pour la plupart des méthodes.|  
  
 L’illustration suivante montre les relations entre les différents états de moteur de script et présente les méthodes qui provoquent des transitions d’un état à un autre.  
  
 L’illustration suivante montre les actions effectuées par le moteur de script durant les différentes transitions d’état.  
  
## <a name="scripting-engine-threading"></a>Threads du moteur de script  
 Un moteur Windows Script pouvant être utilisé dans de nombreux environnements, il est important de conserver son modèle d’exécution le plus flexible possible. Par exemple, un hôte sur un serveur peut avoir besoin de conserver une conception multithread tout en utilisant Windows Script de manière efficace. En même temps, la gestion des threads ne doit pas alourdir un hôte qui n’utilise pas de threads, comme une application type. Pour parvenir à un équilibre approprié, Windows Script limite les méthodes dont dispose un moteur de script à threads libres pour rappeler l’hôte, ce qui libère les hôtes de cette charge.  
  
 Les moteurs de script utilisés sur des serveurs sont généralement implémentés en tant qu’objets COM à threads libres. Cela signifie que les méthodes sur l’interface [IActiveScript](../winscript/reference/iactivescript.md) et ses interfaces associées peuvent être appelées à partir de n’importe quel thread dans le processus, sans marshaling. (Malheureusement, cela signifie également que le moteur de script doit être implémenté en tant que serveur in-process, car OLE ne prend pas en charge le marshaling interprocessus des objets à threads libres.) La synchronisation est la responsabilité du moteur de script. Pour les moteurs de script qui ne sont pas réentrants en interne ou pour les modèles de langage qui ne sont pas multithreads, la synchronisation peut simplement se résumer à la sérialisation de l’accès au moteur de script avec un mutex. Bien entendu, certaines méthodes comme [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) ne doivent pas être sérialisées de cette façon pour permettre à un script bloqué d’être arrêté à partir d’un autre thread.  
  
 Le fait qu’[IActiveScript](../winscript/reference/iactivescript.md) soit généralement à threads libres signifie que l’interface [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) et le modèle objet de l’hôte doivent aussi être à threads libres. Cela rend l’implémentation de l’hôte assez difficile, en particulier dans le cas fréquent où l’hôte est une application Windows monothread avec des contrôles ActiveX monothreads ou de modèle apartment dans son modèle objet. Pour cette raison, les contraintes suivantes sont placées sur l’utilisation de [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) par le moteur de script :  
  
 Le site de script est toujours appelé dans le contexte d’un thread hôte. Autrement dit, le moteur de script n’appelle jamais le site de script dans le contexte d’un thread créé par le moteur de script. Il l’appelle uniquement à partir d’une méthode de moteur de script appelée à partir de l’hôte par le biais d’[IActiveScript](../winscript/reference/iactivescript.md) et de ses dérivés, par le biais de l’objet de répartition du moteur de script exposé, par le biais d’un message Windows ou à partir d’une source d’événement dans le modèle objet de l’hôte.  
  
 Le site du script n’est jamais appelé à partir du contexte d’une méthode de contrôle d’état simple des threads (par exemple, la méthode [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md)) ou à partir de la méthode [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Windows Script, interfaces](../winscript/windows-script-interfaces.md)
