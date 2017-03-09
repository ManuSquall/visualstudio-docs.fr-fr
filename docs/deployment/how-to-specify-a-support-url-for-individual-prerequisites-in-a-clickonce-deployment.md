---
title: "How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, prerequisites"
  - "ClickOnce deployment, URLs"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un déploiement [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] peut vérifier la présence de plusieurs conditions préalables qui doivent être disponibles sur l'ordinateur client afin que l'application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] puisse s'exécuter.  Ces conditions préalables incluent la version minimale obligatoire de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la version du système d'exploitation, et tous les assemblys qui doivent être préinstallés dans le Global Assembly Cache \(GAC\).  Toutefois, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ne peut installer aucun de ces composants requis lui\-même ; si une condition préalable est introuvable, l'installation s'arrête et affiche une boîte de dialogue qui explique pourquoi l'installation a échoué.  
  
 Il existe deux méthodes d'installation des composants requis.  Vous pouvez les installer à l'aide d'une application de programme d'amorçage.  Vous pouvez également spécifier une URL du support technique pour chaque composant requis, cette URL apparaissant dans la boîte de dialogue si le composant requis est introuvable.  La page référencée par cette URL peut contenir des liens vers les instructions d'installation du composant requis.  Si une application ne spécifie aucune URL du support technique pour un composant requis, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affiche l'URL du support technique spécifiée dans le manifeste de déploiement pour l'application dans son ensemble, si elle est définie.  
  
 Alors que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe et MageUI.exe peuvent tous être utilisés pour générer des déploiements [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], aucun de ces outils ne prend directement en charge la spécification d'une URL du support technique pour chaque composant requis.  Ce document décrit comment modifier le manifeste d'application de votre déploiement et le manifeste de déploiement pour inclure ces URL du support technique.  
  
### Spécification d'une URL du support technique pour chaque composant requis  
  
1.  Ouvrez le manifeste d'application \(le fichier .manifest\) pour votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dans un éditeur de texte.  
  
2.  Pour un composant requis du système d'exploitation, ajoutez l'attribut `supportUrl` à l'élément `dependentOS` :  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Pour le composant requis d'une certaine version du Common Language Runtime, ajoutez l'attribut `supportUrl` à l'entrée `dependentAssembly` qui spécifie la dépendance du Common Language Runtime :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Pour le composant requis d'un assembly qui doit être préinstallé dans le Global Assembly Cache, définissez `supportUrl` pour l'élément `dependentAssembly` qui spécifie l'assembly requis :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Facultatif.  Pour les applications qui ciblent .NET Framework 4, ouvrez le manifeste de déploiement \(le fichier .application\) pour votre application [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dans un éditeur de texte.  
  
6.  Pour un composant requis .NET Framework 4, ajoutez l'attribut `supportUrl` à l'élément `compatibleFrameworks` :  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Une fois que vous avez modifié manuellement le manifeste d'application, vous devez signer de nouveau le manifeste d'application à l'aide de votre certificat numérique, puis mettre à jour et signer de nouveau le manifeste de déploiement.  Vous devez utiliser les outils du Kit de développement logiciel \(SDK\) Mage.exe ou MageUI.exe pour accomplir cette tâche, car la régénération de ces fichiers à l'aide de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] efface vos modifications manuelles.  Pour plus d'informations sur l'utilisation de Mage.exe pour resigner les manifestes, consultez [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Sécurité .NET Framework  
 L'URL du support technique n'apparaît pas dans la boîte de dialogue si l'application est marquée pour s'exécuter avec une confiance partielle.  
  
## Voir aussi  
 [Mage.exe \(outil Manifest Generation and Editing\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> Element](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Composants requis pour le déploiement d'applications](../deployment/application-deployment-prerequisites.md)