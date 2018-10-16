---
title: 'Comment : spécifier une URL de prise en charge pour chaque composant requis dans un déploiement ClickOnce | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: d6b7f9c9f718b0f76d2a2b0c313c951064c5dc6f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262260"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Comment : spécifier une URL du support technique pour chaque composant requis lors d'un déploiement ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiement peut tester plusieurs conditions préalables qui doivent être disponibles sur l’ordinateur client pour le [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application de s’exécuter. Citons notamment la version minimale requise de la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], la version du système d’exploitation et tous les assemblys qui doivent être préinstallés dans le global assembly cache (GAC). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], toutefois, ne peut pas installer un de ces conditions préalables lui-même ; Si une condition préalable n’est trouvée, il simplement arrête l’installation et affiche une boîte de dialogue expliquant pourquoi l’installation a échoué.  
  
 Il existe deux méthodes pour l’installation des composants requis. Vous pouvez les installer à l’aide d’un programme d’amorçage. Vous pouvez également spécifier une URL de prise en charge pour chaque composant requis, ce qui est affichée aux utilisateurs sur la boîte de dialogue si le composant requis est introuvable. La page référencée par cette URL peut contenir des liens vers des instructions d’installation du composant requis. Si une application ne spécifie pas une URL de prise en charge pour un composant requis, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] affiche l’URL de prise en charge spécifiée dans le manifeste de déploiement pour l’application dans son ensemble, si elle est définie.  
  
 Bien que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], Mage.exe et MageUI.exe peuvent tous être utilisés pour générer [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] déploiements, aucun de ces outils ne prend directement en charge en spécifiant une URL de prise en charge pour chaque composant requis. Ce document décrit comment modifier votre déploiement manifeste d’application et manifeste de déploiement pour inclure ces URL du support technique.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Spécification d’une URL de prise en charge pour un composant requis  
  
1.  Ouvrez le manifeste d’application (le fichier .manifest) pour votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application dans un éditeur de texte.  
  
2.  Pour un composant requis du système d’exploitation, ajoutez le `supportUrl` attribut le `dependentOS` élément :  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Pour une condition préalable pour une version spécifique du common language runtime, ajoutez le `supportUrl` attribut le `dependentAssembly` entrée qui spécifie la dépendance du common language runtime :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Pour un composant requis pour un assembly qui doit être préinstallé dans le global assembly cache, définissez le `supportUrl` pour le `dependentAssembly` élément qui spécifie l’assembly requis :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Facultatif. Pour les applications qui ciblent le .NET Framework 4, ouvrez le manifeste de déploiement (le fichier .application) pour votre [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] application dans un éditeur de texte.  
  
6.  Pour une condition préalable de .NET Framework 4, ajoutez le `supportUrl` attribut le `compatibleFrameworks` élément :  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Une fois que vous avez modifié manuellement le manifeste d’application, vous devez signer à nouveau le manifeste d’application à l’aide de votre certificat numérique, puis mettre à jour et signer à nouveau le manifeste de déploiement. Vous devez utiliser Mage.exe ou MageUI.exe SDK pour accomplir cette tâche, comme la régénération de ces fichiers à l’aide des outils [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] efface vos modifications manuelles. Pour plus d’informations sur l’utilisation de Mage.exe pour resigner des manifestes, consultez [Comment : re-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 L’URL du support technique ne figure pas dans la boîte de dialogue si l’application est marquée pour s’exécuter en mode de confiance partielle.  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (outil Manifest Generation and Editing)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > élément](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)



