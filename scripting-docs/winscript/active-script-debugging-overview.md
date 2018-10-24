---
title: Présentation du débogage de script actif | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 447a8faf6e62448e7e8ce9ee8d7d8097fba2dd7b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919362"
---
# <a name="active-script-debugging-overview"></a>Débogage de script actif (présentation)
Les interfaces de débogage de script actif permettent d’effectuer un débogage indépendant du langage et indépendant de l’hôte, et elles prennent en charge un large éventail d’environnements de développement.  
  
 ![Processus Script Host](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Figure 1  
  
 Un environnement de débogage indépendant du langage peut prendre en charge n’importe quel langage ou combinaison de langages de programmation, sans avoir aucune connaissance spécifique de ces langages de programmation. L’environnement de débogage prend également en charge les points d’arrêt et l’exécution pas à pas interlangage. (Cette présentation se concentre essentiellement sur la prise en charge des langages de script, tels que VBScript et [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].)  
  
 Un débogueur indépendant de l’hôte peut être utilisé automatiquement avec n’importe quel hôte Active Scripting, tel qu’Internet Explorer ou un hôte personnalisé. L’hôte contrôle ce que le débogueur présente à l’utilisateur, de la structure de l’arborescence de documents jusqu’au contenu et à la coloration syntaxique des documents de débogage. Cela permet d’afficher le code source débogué dans le contexte du document hôte. Par exemple, Internet Explorer peut afficher un script dans une page HTML.  
  
 Les sous-sections qui suivent décrivent chaque composant clé de débogage actif et ses interfaces associées. Toutefois, avant de continuer, nous devons définir plusieurs concepts clés du débogage actif :  
  
 application hôte  
 Application qui héberge les moteurs de script et fournit un ensemble d’objets scriptable (ou « modèle objet »).  
  
 Moteur de langage  
 Composant qui fournit les abstractions de débogage, d’analyse et d’exécution pour un langage particulier.  
  
 IDE de débogueur  
 Application qui fournit l’interface utilisateur de débogage en communiquant avec l’application hôte et les moteurs de langage.  
  
 Gestionnaire de débogage d’ordinateur  
 Composant qui tient à jour un registre des processus d’application pouvant être débogués.  
  
 Gestionnaire de débogage de processus  
 Composant qui tient à jour l’arborescence de documents pouvant être débogués pour une application particulière, qui effectue le suivi des threads en cours d’exécution, et ainsi de suite.  
  
 Contexte de document  
 Un contexte de document est une abstraction représentant une plage spécifique dans le code source d’un document hôte.  
  
 Contexte de code  
 Un contexte de code représente un emplacement particulier dans le code en cours d’exécution d’un moteur de langage (un « pointeur d’instruction virtuel ».)  
  
 Contexte d’expression  
 Contexte particulier (par exemple un frame de pile) dans lequel les expressions peuvent être évaluées par un moteur de langage.  
  
 Exploration des objets  
 Représentation structurée et indépendante du langage du nom, du type, de la valeur et des sous-objets d’un objet, et qui convient à l’implémentation d’une interface utilisateur de « fenêtre Espion ».  
  
 Vous trouverez ci-dessous une présentation de chacun des principaux composants du débogage actif et des interfaces associées correspondantes, suivie des détails de ces interfaces.  
  
## <a name="language-engine"></a>Moteur de langage  
 Le moteur de langage fournit ce qui suit :  
  
- Analyse du langage et exécution  
  
- Prise en charge du débogage (points d’arrêt et ainsi de suite)  
  
- Évaluation des expressions  
  
- Coloration syntaxique  
  
- Exploration des objets  
  
- Énumération de la pile et analyse  
  
  Voici la liste des interfaces qu’un moteur de script doit prendre en charge pour fournir le débogage, l’évaluation des expressions et l’exploration des objets. Ces interfaces sont utilisées par l’application hôte pour établir un mappage entre son contexte de document et les contextes de code du moteur, et également par l’interface utilisateur du débogueur pour effectuer l’évaluation des expressions, l’énumération de la pile et l’exploration des objets.  
  
  [Interface IActiveScriptDebug](../winscript/reference/iactivescriptdebug-interface.md)  
  Fournit la coloration syntaxique et l’énumération du contexte de code.  
  
  [Interface IActiveScriptErrorDebug](../winscript/reference/iactivescripterrordebug-interface.md)  
  Retourne les contextes de document et les frames de pile en cas d’erreur.  
  
  [Interface IActiveScriptSiteDebug](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Lien fourni par l’hôte du moteur de script vers le débogueur.  
  
  [Interface IDebugCodeContext](../winscript/reference/idebugcodecontext-interface.md)  
  Fournit un « pointeur d’instruction » virtuel dans un thread.  
  
  [Interface IEnumDebugCodeContexts](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Énumère les contextes de code qui correspondent à un contexte de document.  
  
  [Interface IDebugStackFrame](../winscript/reference/idebugstackframe-interface.md)  
  Représente un frame de pile logique sur la pile des threads.  
  
  [Interface IDebugExpressionContext](../winscript/reference/idebugexpressioncontext-interface.md)  
  Fournit le contexte dans lequel les expressions peuvent être évaluées.  
  
  [Interface IDebugStackFrameSniffer](../winscript/reference/idebugstackframesniffer-interface.md)  
  Fournit un moyen d’énumérer les frames de pile logiques.  
  
  [Interface IDebugExpression](../winscript/reference/idebugexpression-interface.md)  
  Représente une expression évaluée de façon asynchrone.  
  
  [Interface IDebugSyncOperation](../winscript/reference/idebugsyncoperation-interface.md)  
  Permet à un moteur de script d’extraire une opération qui doit être effectuée pendant qu’elle est imbriquée dans un thread bloqué particulier.  
  
  [Interface IDebugAsyncOperation](../winscript/reference/idebugasyncoperation-interface.md)  
  Fournit un accès asynchrone à une opération de débogage synchrone.  
  
  [Interface IDebugAsyncOperationCallBack](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Fournit des événements d’état liés à la progression d’une évaluation d’interface `IDebugAsyncOperation`.  
  
  [Interface IEnumDebugExpressionContexts](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Énumère une collection d’objets `IDebugExpressionContexts`.  
  
  [Interface IProvideExpressionContexts](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Fournit un moyen d’énumérer les contextes d’expression connus d’un certain composant.  
  
  [Interface IDebugFormatter](../winscript/reference/idebugformatter-interface.md)  
  Permet à un langage ou à un IDE de personnaliser la conversion entre des valeurs de type VARIANT ou des types VARTYPE et des chaînes.  
  
  [Interface IDebugStackFrameSnifferEx](../winscript/reference/idebugstackframesnifferex-interface.md)  
  Énumère les frames de pile logiques pour le gestionnaire de débogage de processus.  
  
## <a name="hosts"></a>Hôtes  
 L’hôte :  
  
- Héberge les moteurs de langage.  
  
- Fournit un modèle objet (ensemble d’objets qui peuvent être scriptés).  
  
- Définit une arborescence de documents pouvant être débogués, et leur contenu.  
  
- Organise les scripts dans des applications virtuelles.  
  
  Il existe deux sortes d’hôtes :  
  
- Un hôte passif prend en charge uniquement les interfaces Active Scripting de base. Il n’a aucun contrôle sur l’organisation ou la structure des documents. Celles-ci sont déterminées entièrement par les scripts fournis aux moteurs de langage.  
  
- Un hôte intelligent prend en charge un plus grand ensemble d’interfaces, ce qui lui permet de définir l’arborescence de documents, le contenu des documents et la coloration syntaxique. Il existe un ensemble d’interfaces d’assistance, décrites dans la sous-section suivante, qui permettent à un hôte de devenir très facilement un hôte intelligent.  
  
### <a name="smart-host-helper-interfaces"></a>Interfaces d’assistance d’hôte intelligent  
 Les méthodes `IDebugDocumentHelper` fournissent un ensemble simplifié d’interfaces qu’un hôte peut utiliser pour bénéficier des avantages offerts par l’hébergement intelligent sans avoir à gérer toute la complexité (et la puissance) de toute les interfaces d’hôte.  
  
 Un hôte n’est bien entendu pas obligé d’utiliser ces interfaces. Toutefois, le recours à ces interfaces peut éviter d’avoir à implémenter ou à utiliser certaines interfaces plus complexes.  
  
 [Interface IDebugDocumentHelper](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implémentée par le gestionnaire de débogage de processus, elle fournit des implémentations pour de nombreuses interfaces nécessaires pour l’hébergement intelligent.  
  
 [Interface IDebugDocumentHost](../winscript/reference/idebugdocumenthost-interface.md)  
 Implémentée (de manière facultative) par l’hôte pour exposer au débogueur une fonctionnalité qui est propre à l’hôte, telle que la coloration syntaxique.  
  
 Pour plus d’informations, consultez [Implémentation des interfaces d’assistance d’hôte intelligent](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Interfaces complètes d’hôte intelligent  
 Vous trouverez ci-dessous l’ensemble complet des interfaces qu’un hôte intelligent doit implémenter ou utiliser s’il n’utilise pas les interfaces d’assistance.  
  
 Interfaces implémentées par l’hôte :  
  
 [Interface IDebugDocumentInfo](../winscript/reference/idebugdocumentinfo-interface.md)  
 Fournit des informations sur un document, qui peut être ou ne pas être instancié.  
  
 [Interface IDebugDocumentProvider](../winscript/reference/idebugdocumentprovider-interface.md)  
 Permet d’instancier un document à la demande.  
  
 [Interface IDebugDocument](../winscript/reference/idebugdocument-interface.md)  
 Interface de base pour tous les documents de débogage.  
  
 [Interface IDebugDocumentText](../winscript/reference/idebugdocumenttext-interface.md)  
 Fournit l’accès à une version « texte uniquement » du document de débogage.  
  
 [Interface IDebugDocumentTextAuthor](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Autorise la modification de la version « texte uniquement » du document de débogage.  
  
 [Interface IDebugDocumentContext](../winscript/reference/idebugdocumentcontext-interface.md)  
 Fournit une représentation abstraite d’une partie du document en cours de débogage.  
  
 Interfaces implémentées par le gestionnaire de débogage de processus pour le compte de l’hôte :  
  
 [Interface IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
 Étend la fonctionnalité de l’interface `IDebugDocumentProvider` en fournissant un contexte dans une arborescence de projet.  
  
## <a name="debugger-ide"></a>IDE de débogueur  
 L’IDE est une interface utilisateur de débogage indépendante du langage. Elle offre les possibilités suivantes :  
  
- Visionneuses/éditeurs de documents  
  
- Gestion des points d’arrêt  
  
- Évaluation des expressions et fenêtres Espion  
  
- Exploration des frames de pile  
  
- Exploration de classes/objets  
  
- Exploration de la structure des applications virtuelles  
  
  Interfaces implémentées par le débogueur :  
  
  [Interface IApplicationDebugger](../winscript/reference/iapplicationdebugger-interface.md)  
  Interface principale exposée par une session d’IDE de débogueur.  
  
  [Interface IApplicationDebuggerUI](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Procure à un composant externe davantage de contrôle sur l’interface utilisateur du débogueur.  
  
  [Interface IDebugExpressionCallBack](../winscript/reference/idebugexpressioncallback-interface.md)  
  Fournit des événements d’état pour la progression de l’évaluation de `IDebugExpression`.  
  
  [Interface IDebugDocumentTextEvents](../winscript/reference/idebugdocumenttextevents-interface.md)  
  Fournit des événements indiquant les modifications qui ont été apportées au document de texte associé.  
  
  [Interface IDebugApplicationNodeEvents](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Fournit l’interface d’événement pour l’interface `IDebugApplicationNode`.  
  
### <a name="machine-debug-manager"></a>Gestionnaire de débogage d’ordinateur  
 Le gestionnaire de débogage d’ordinateur fournit le point de connexion entre les applications virtuelles et les débogueurs en tenant à jour et en dressant une liste des applications virtuelles actives.  
  
 [Interface IDebugSessionProvider](../winscript/reference/idebugsessionprovider-interface.md)  
 Établit une session de débogage pour une application en cours d’exécution.  
  
 [Interface IMachineDebugManager](../winscript/reference/imachinedebugmanager-interface.md)  
 Interface principale avec le gestionnaire de débogage d’ordinateur.  
  
 [Interface IMachineDebugManagerCookie](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Semblable à `IMachineDebugManager`, mais cette interface prend en charge les cookies de débogage.  
  
 [Interface IMachineDebugManagerEvents](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Signale les modifications apportées à la liste des applications en cours d’exécution tenue à jour par le gestionnaire de débogage d’ordinateur.  
  
 [Interface IEnumRemoteDebugApplications](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Énumère les applications en cours d’exécution sur un ordinateur.  
  
### <a name="process-debug-manager"></a>Gestionnaire de débogage de processus  
 Le gestionnaire de débogage de processus effectue les opérations suivantes :  
  
- Il synchronise le débogage de plusieurs moteurs de langage.  
  
- Il tient à jour une arborescence de documents pouvant être débogués.  
  
- Il fusionne les frames de pile.  
  
- Il coordonne les points d’arrêt et l’exécution pas à pas dans les moteurs de langage.  
  
- Il effectue le suivi des threads.  
  
- Il gère un thread de débogueur pour le traitement asynchrone.  
  
- Il communique avec le gestionnaire de débogage d’ordinateur et l’IDE de débogueur.  
  
  Voici les interfaces fournies par le gestionnaire de débogage de processus.  
  
  [Interface IProcessDebugManager](../winscript/reference/iprocessdebugmanager-interface.md)  
  Interface principale avec le gestionnaire de débogage de processus. Cette interface peut créer, ajouter ou supprimer une application virtuelle d’un processus.  
  
  [Interface IRemoteDebugApplication](../winscript/reference/iremotedebugapplication-interface.md)  
  Représente une application en cours d’exécution.  
  
  [Interface IDebugApplication](../winscript/reference/idebugapplication-interface.md)  
  Expose des méthodes de débogage non accessibles à distance en vue d’une utilisation par les hôtes et les moteurs de langage.  
  
  [Interface IRemoteDebugApplicationThread](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Représente un thread d’exécution dans une application donnée.  
  
  [Interface IDebugApplicationThread](../winscript/reference/idebugapplicationthread-interface.md)  
  Permet aux moteurs de langage et aux hôtes d’assurer la synchronisation des threads et de tenir à jour les informations d’état de débogage propres aux threads.  
  
  [Interface IEnumRemoteDebugApplicationThreads](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Énumère les threads en cours d’exécution dans une application.  
  
  [Interface IDebugThreadCall](../winscript/reference/idebugthreadcall-interface.md)  
  Distribue les appels marshalés.  
  
  [Interface IDebugApplicationNode](../winscript/reference/idebugapplicationnode-interface.md)  
  Conserve une position pour un document dans la hiérarchie.  
  
  [Interface IEnumDebugApplicationNodes](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Énumère les nœuds enfants d’un nœud associé à une application.  
  
  [Interface IEnumDebugStackFrames](../winscript/reference/ienumdebugstackframes-interface.md)  
  Énumère les frames de pile correspondant à un thread, fusionnés à partir des moteurs.  
  
  [Interface IDebugCookie](../winscript/reference/idebugcookie-interface.md)  
  Permet de définir le cookie de débogage dans les débogueurs de script.  
  
  [Interface IDebugHelper](../winscript/reference/idebughelper-interface.md)  
  Sert de fabrique pour les explorateurs d’objets et points de connexion simples pour les moteurs de script.  
  
  [Interface ISimpleConnectionPoint](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Fournit un moyen simple de décrire et d’énumérer les événements déclenchés sur un point de connexion particulier, pour les moteurs de script.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogueur de script actif](../winscript/reference/active-script-debugger-interfaces.md)