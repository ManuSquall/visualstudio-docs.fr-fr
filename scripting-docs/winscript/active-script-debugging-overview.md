---
title: "D&#233;bogage de script actif, pr&#233;sentation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Débogage de script actif (présentation)"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# D&#233;bogage de script actif, pr&#233;sentation
Les interfaces de débogage de script actif permettent le débogage indépendante du langage et hôte neutre, et prennent en charge une large gamme d'environnements de développement.  
  
 ![Processus Script Host](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
Figure 1  
  
 Un environnement de débogage indépendant du langage peut prendre en charge n'importe quel langage de programmation ou combinaison des langages de programmation, sans avoir une connaissance spécifique de l'un de ces langages.  L'environnement de débogage prend également en charge la progression interlangage et les points d'arrêt.  \(Cette vue d'ensemble traite principalement sur les langages de script en charge, tels que et [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]VBScript.\)  
  
 Un débogueur hôte neutre peut être utilisé automatiquement avec tout hôte d'Active Scripting, tel qu'Internet Explorer ou un hôte personnalisé.  Les contrôles hôtes que le débogueur présente à l'utilisateur, de la structure de l'arborescence de documents au contenu et la coloration de syntaxe du débogage documents.  Cela permet au code source débogué à afficher dans le contexte du document hôte.  Par exemple, Internet Explorer peut afficher un script dans une page HTML.  
  
 Dans les sous\-sections ci\-dessous, chaque composant clé dans le débogage active et ses interfaces associées sont traités.  Toutefois, avant de continuer davantage, clé plusieurs des concepts actifs de débogage doivent être définis :  
  
 application hôte  
 L'application qui héberge les moteurs de script et fournit un ensemble scriptable d'objets \(ou « modèle objet »\).  
  
 moteur de langage  
 Un composant qui fournit l'analyse, l'exécution, et les abstractions de débogage pour un langage particulier.  
  
 débogueur IDE  
 L'application qui fournit le débogage interface utilisateur par la communication avec l'application et les moteurs de langage hôte.  
  
 l'ordinateur de débogage le gestionnaire  
 Un composant qui gère un Registre des processus d'application débogable.  
  
 le processus de débogage le gestionnaire  
 Un composant qui gère l'arborescence de documents débogable pour une application particulière, effectue les threads en cours de exécution, et ainsi de suite.  
  
 contexte de document  
 Un contexte de document est une abstraction représentant une plage spécifique dans le code source d'un document hôte.  
  
 contexte de code  
 Un contexte de code représente un emplacement particulier dans le code en cours de exécution d'un moteur de langue \(« pointeur d'instruction virtuel ».\)  
  
 contexte d'expression  
 Un contexte particulier \(par exemple, un frame de pile\) dans lequel les expressions peuvent être évaluées par un moteur de langage.  
  
 objet parcourant  
 Une représentation d'un nom d'objet, un type, une valeur, et des sous\-objets structurés et LINQ indépendants, appropriés pour implémenter une « fenêtre Espion » interface utilisateur.  
  
 Vous trouverez ci\-dessous une présentation de chacune des composants principaux actifs et de correspondre de débogage, les interfaces associées, suivies des détails de ces interfaces.  
  
## Moteur de langage  
 Le moteur de langage le fournit :  
  
-   Analyse et exécution de langage.  
  
-   Prise en charge du débogage \(points d'arrêt etc.\).  
  
-   Évaluation de l'expression.  
  
-   Coloration de syntaxe.  
  
-   Objet parcourir.  
  
-   Énumération et analyse de pile.  
  
 Vous trouverez ci\-dessous les interfaces qu'un moteur de script doit prendre en charge pour fournir le débogage, l'évaluation de l'expression, et l'objet parcourir.  Ces interfaces sont utilisées par l'application hôte de mappage entre son contexte de document et les contextes de code du moteur, et également par le débogueur interface utilisateur de faire l'évaluation de l'expression, l'énumération de pile, et l'objet parcourir.  
  
 [IActiveScriptDebug, interface](../winscript/reference/iactivescriptdebug-interface.md)  
 Fournit l'énumération de coloration de syntaxe et de contexte de code.  
  
 [IActiveScriptErrorDebug, interface](../winscript/reference/iactivescripterrordebug-interface.md)  
 Contextes de document et frames de pile de retour des erreurs.  
  
 [IActiveScriptSiteDebug, interface](../winscript/reference/iactivescriptsitedebug-interface.md)  
 Lien fourni par hôte du moteur de script au débogueur.  
  
 [IDebugCodeContext, interface](../winscript/reference/idebugcodecontext-interface.md)  
 Fournit un « pointeur d'instruction » virtuel dans un thread.  
  
 [IEnumDebugCodeContexts, interface](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 Énumère les contextes de code qui correspondent à un contexte de document.  
  
 [IDebugStackFrame, interface](../winscript/reference/idebugstackframe-interface.md)  
 Représente un frame de pile logique sur la pile des threads.  
  
 [IDebugExpressionContext, interface](../winscript/reference/idebugexpressioncontext-interface.md)  
 Fournit la zone dans lequel les expressions peuvent être évaluées.  
  
 [IDebugStackFrameSniffer, interface](../winscript/reference/idebugstackframesniffer-interface.md)  
 Permet d'énumérer les frames de pile logiques.  
  
 [IDebugExpression, interface](../winscript/reference/idebugexpression-interface.md)  
 Représente une expression évaluée de façon asynchrone.  
  
 [IDebugSyncOperation, interface](../winscript/reference/idebugsyncoperation-interface.md)  
 Permet à un moteur de script pour abréger une opération qui doit être exécutée pendant qu'imbriquée dans un thread bloqué particulier.  
  
 [IDebugAsyncOperation, interface](../winscript/reference/idebugasyncoperation-interface.md)  
 Fournit l'accès à une opération asynchrone de débogage synchrone.  
  
 [IDebugAsyncOperationCallBack, interface](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 Fournit des événements de mode rapport avec la progression d'une évaluation d'interface d' `IDebugAsyncOperation` .  
  
 [IEnumDebugExpressionContexts, interface](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 Énumère une collection d'objets `IDebugExpressionContexts` .  
  
 [IProvideExpressionContexts, interface](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 Permet d'énumérer des contextes d'expression connus par un certain composant.  
  
 [IDebugFormatter, interface](../winscript/reference/idebugformatter-interface.md)  
 Permet à un langage ou l'IDE pour personnaliser la conversion entre les valeurs VARIANTES ou les types et les chaînes de VARTYPE.  
  
 [IDebugStackFrameSnifferEx, interface](../winscript/reference/idebugstackframesnifferex-interface.md)  
 Énumère les frames de pile logiques de le PDM.  
  
## Hôtes  
 L'hôte :  
  
-   Héberge les moteurs de langage.  
  
-   Fournit un modèle objet \(a des objets qui peuvent être écrits\).  
  
-   Définit une arborescence de documents qui peuvent être débogué et de leur contenu.  
  
-   Organise les scripts dans des applications virtuelles.  
  
 Il existe deux types d'hôtes :  
  
-   Un hôte muet prend en charge uniquement les interfaces de base d'Active Scripting.  Il n'a aucun contrôle de structure du document ou d'organisations ; cela est entièrement déterminé par les scripts fournis aux moteurs de langage.  
  
-   Un hôte intelligent prend en charge un plus grand ensemble d'interfaces qui lui permet de définir l'arborescence de documents, le contenu du document, et la coloration de syntaxe.  Il existe un jeu d'interfaces d'assistance, décrit dans la section sous\-section, qui facilitent de nombreuses pour qu'un hôte soit un intelligent hôte.  
  
### Interfaces d'assistance de SMART\-hôte  
 Les méthodes d' `IDebugDocumentHelper` fournissent un jeu d'interfaces considérablement simplifié qu'un hôte peut utiliser pour obtenir les avantages du SMART\- hébergement sans gérer la complexité complète \(et l'alimentation\) des interfaces hôtes complètes.  
  
 Un hôte n'est pas nécessaire d'utiliser ces interfaces, naturellement.  Toutefois à l'aide de ces interfaces peut éviter d'implémenter ou utiliser un nombre quelconque d'interfaces plus complexes.  
  
 [IDebugDocumentHelper, interface](../winscript/reference/idebugdocumenthelper-interface.md)  
 Implémentée par PDM et fournit des implémentations pour de nombreuses interfaces nécessaires pour l'hébergement intelligent.  
  
 [IDebugDocumentHost, interface](../winscript/reference/idebugdocumenthost-interface.md)  
 Implémenté \(facultatif\) par l'hôte pour exposer les fonctionnalités d'hôte spécifique, telle que la coloration de syntaxe, le débogueur.  
  
 Pour plus d'informations, consultez [Implémentation des interfaces d'assistance d'hôte intelligent](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### Interfaces complètes de SMART\-hôte  
 Voici l'ensemble des interfaces qu'un SMART\- hôte doit implémenter ou utiliser s'il n'utilise pas les interfaces d'assistance.  
  
 Interfaces implémentées par l'hôte :  
  
 [IDebugDocumentInfo, interface](../winscript/reference/idebugdocumentinfo-interface.md)  
 Fournit des informations sur un document, qui peut ou ne peut être instancié.  
  
 [IDebugDocumentProvider, interface](../winscript/reference/idebugdocumentprovider-interface.md)  
 Fournit le moyen d'instancier un document à la demande.  
  
 [IDebugDocument, interface](../winscript/reference/idebugdocument-interface.md)  
 Toute interface de base pour les versions debug des documents.  
  
 [IDebugDocumentText, interface](../winscript/reference/idebugdocumenttext-interface.md)  
 Permet d'accéder à une version texte uniquement du document de débogage.  
  
 [IDebugDocumentTextAuthor, interface](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Permet la modification de la version texte uniquement du document de débogage.  
  
 [IDebugDocumentContext, interface](../winscript/reference/idebugdocumentcontext-interface.md)  
 Fournit une représentation abstraite d'une partie du document en cours de débogage.  
  
 Interfaces implémentées par PDM de la part de l'hôte :  
  
 [IDebugApplicationNode, interface](../winscript/reference/idebugapplicationnode-interface.md)  
 Étend les fonctionnalités de l'interface d' `IDebugDocumentProvider` en fournissant une zone dans une arborescence du projet.  
  
## Débogueur IDE  
 L'IDE est un débogage langage indépendant interface utilisateur.  Il fournit :  
  
-   Visionneuses\/éditeurs de document.  
  
-   Gestion de point d'arrêt.  
  
-   Évaluation de l'expression et fenêtres Espion.  
  
-   Frame de pile parcourir.  
  
-   Objet\/classe parcourir.  
  
-   Recherche de la structure virtuelle d'application.  
  
 Interfaces implémentées par le débogueur :  
  
 [IApplicationDebugger, interface](../winscript/reference/iapplicationdebugger-interface.md)  
 L'interface principale exposée par une session IDE de débogueur.  
  
 [IApplicationDebuggerUI, interface](../winscript/reference/iapplicationdebuggerui-interface.md)  
 Permet à un composant externe plus de contrôle de l'interface utilisateur \(UI\) du débogueur.  
  
 [IDebugExpressionCallBack, interface](../winscript/reference/idebugexpressioncallback-interface.md)  
 Fournit des événements d'état pour la progression d'évaluation d' `IDebugExpression` .  
  
 [IDebugDocumentTextEvents, interface](../winscript/reference/idebugdocumenttextevents-interface.md)  
 Fournit des événements qui indique les modifications apportées au document texte associé.  
  
 [IDebugApplicationNodeEvents, interface](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 Fournit l'interface d'événement pour l'interface d' `IDebugApplicationNode` .  
  
### Debug Machine Manager  
 L'ordinateur de débogage le gestionnaire fournit le point de liaison entre les applications virtuelles et les débogueurs en mettant à jour et en énumérant une liste d'applications virtuelles actives.  
  
 [IDebugSessionProvider, interface](../winscript/reference/idebugsessionprovider-interface.md)  
 Génère une session de débogage pour une application active.  
  
 [IMachineDebugManager, interface](../winscript/reference/imachinedebugmanager-interface.md)  
 L'interface principale à l'ordinateur de débogage le gestionnaire.  
  
 [IMachineDebugManagerCookie, interface](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 Semblable à l'interface d' `IMachineDebugManager`, mais à cette interface prend en charge le débogage des cookies.  
  
 [IMachineDebugManagerEvents, interface](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Les modifications de signaux de la liste d'application active mise à jour par l'ordinateur de débogage le gestionnaire.  
  
 [IEnumRemoteDebugApplications, interface](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Énumère les applications actives sur un ordinateur.  
  
### Process Debug Manager  
 Le PDM effectue les opérations suivantes :  
  
-   Synchronise le débogage de plusieurs moteurs de langage.  
  
-   Met à jour une arborescence de documents débogable.  
  
-   Fusionne des frames de pile.  
  
-   Points d'arrêt de coordonnées et progression entre les moteurs de langage.  
  
-   Thread de suivi.  
  
-   Met à jour un thread de débogueur pour le traitement asynchrone.  
  
-   Communique avec l'ordinateur de débogage le pilote et le débogueur IDE.  
  
 Voici les interfaces fournies par le processus de débogage le gestionnaire.  
  
 [IProcessDebugManager, interface](../winscript/reference/iprocessdebugmanager-interface.md)  
 L'interface principale au processus de débogage le gestionnaire.  Cette interface peut créer, ajouter, supprimer ou une application virtuelle d'un processus.  
  
 [IRemoteDebugApplication, interface](../winscript/reference/iremotedebugapplication-interface.md)  
 Représente une application active.  
  
 [IDebugApplication, interface](../winscript/reference/idebugapplication-interface.md)  
 Expose les méthodes non exécutables à distance de débogage pour une utilisation par les moteurs de langage et les hôtes.  
  
 [IRemoteDebugApplicationThread, interface](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 Représente un thread d'exécution dans une application particulière.  
  
 [IDebugApplicationThread, interface](../winscript/reference/idebugapplicationthread-interface.md)  
 Permet aux moteurs de langage et aux hôtes pour fournir la synchronisation des threads et mettre à jour le thread\- spécifique, les informations de débogage point\- état.  
  
 [IEnumRemoteDebugApplicationThreads, interface](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 Énumère les threads en cours de exécution dans une application.  
  
 [IDebugThreadCall, interface](../winscript/reference/idebugthreadcall-interface.md)  
 Appels marshalés par expéditions.  
  
 [IDebugApplicationNode, interface](../winscript/reference/idebugapplicationnode-interface.md)  
 Met à jour une position d'un document dans la hiérarchie.  
  
 [IEnumDebugApplicationNodes, interface](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 Énumère les nœuds enfants d'un nœud connexe avec une application.  
  
 [IEnumDebugStackFrames, interface](../winscript/reference/ienumdebugstackframes-interface.md)  
 Énumère les frames de pile correspondant à un thread, fusionné des moteurs.  
  
 [IDebugCookie, interface](../winscript/reference/idebugcookie-interface.md)  
 Permet le cookie de débogage à définir dans les débogueurs de script.  
  
 [IDebugHelper, interface](../winscript/reference/idebughelper-interface.md)  
 Sert de fabrique aux navigateurs d'objet et aux points de connexion simples pour les moteurs de script.  
  
 [ISimpleConnectionPoint, interface](../winscript/reference/isimpleconnectionpoint-interface.md)  
 Offre un moyen simple pour décrire et énumérer les événements déclenchés sur le point de connexion particulier, pour les moteurs de script.  
  
## Voir aussi  
 [Débogueur de script actif, interfaces](../winscript/reference/active-script-debugger-interfaces.md)