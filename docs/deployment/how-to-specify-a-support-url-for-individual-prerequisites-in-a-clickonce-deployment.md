---
title: 'Comment : spécifier une URL de prise en charge pour chaque composant requis dans un déploiement ClickOnce | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 86d4b765dc5e6c56fdc8e7a3b082afaa72accf49
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Comment : spécifier une URL du support technique pour chaque composant requis lors d'un déploiement ClickOnce
A [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiement peut vérifier la présence de plusieurs conditions préalables qui doivent être disponibles sur l’ordinateur client pour le [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application de s’exécuter. Ceux-ci incluent la version minimale requise de la [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], la version du système d’exploitation et tous les assemblys qui doivent être préinstallés dans le global assembly cache (GAC). [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], toutefois, ne peut pas installer un de ces composants requis lui-même ; Si une condition préalable n’est trouvée, il simplement arrête l’installation et affiche une boîte de dialogue expliquant pourquoi l’installation a échoué.  
  
 Il existe deux méthodes pour installer les composants requis. Vous pouvez les installer à l’aide d’une application du programme d’amorçage. Vous pouvez également spécifier une URL de prise en charge pour chaque composant requis, qui est affichée aux utilisateurs sur la boîte de dialogue si le composant requis est introuvable. La page référencée par cette URL peut contenir des liens vers des instructions pour l’installation du composant requis. Si une application ne spécifie pas une URL de prise en charge pour un composant requis, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] affiche l’URL de prise en charge spécifiée dans le manifeste de déploiement pour l’application dans son ensemble, si elle est définie.  
  
 Alors que [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe et MageUI.exe peuvent tous être utilisés pour générer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] déploiements, aucun de ces outils ne prend directement en charge la spécification d’une URL de prise en charge pour chaque composant requis. Ce document décrit comment modifier votre déploiement manifeste d’application et le manifeste de déploiement pour inclure ces URL du support technique.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Spécification d’une URL de prise en charge pour un composant requis  
  
1.  Ouvrez le manifeste d’application (le fichier .manifest) pour votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application dans un éditeur de texte.  
  
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
  
3.  Pour le composant requis d’une certaine version du common language runtime, vous devez ajouter le `supportUrl` attribut le `dependentAssembly` entrée qui spécifie la dépendance du common language runtime :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Pour le composant requis d’un assembly qui doit être préinstallé dans le global assembly cache, définissez la `supportUrl` pour la `dependentAssembly` élément qui spécifie l’assembly requis :  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Facultatif. Pour les applications qui ciblent le .NET Framework 4, ouvrez le manifeste de déploiement (fichier .application) pour votre [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] application dans un éditeur de texte.  
  
6.  Pour le composant requis .NET Framework 4, vous devez ajouter le `supportUrl` attribut le `compatibleFrameworks` élément :  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Une fois que vous avez modifié manuellement le manifeste d’application, vous devez signer de nouveau le manifeste d’application à l’aide de votre certificat numérique, puis mettre à jour et signer à nouveau le manifeste de déploiement. Vous devez utiliser Mage.exe ou MageUI.exe SDK pour accomplir cette tâche, car la régénération de ces fichiers à l’aide des outils [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] efface vos modifications manuelles. Pour plus d’informations sur l’utilisation de Mage.exe pour signer à nouveau les manifestes, consultez [Comment : signer de nouveau l’Application et les manifestes de déploiement](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 L’URL du support technique ne figure pas dans la boîte de dialogue si l’application est marquée pour s’exécuter avec une confiance partielle.  
  
## <a name="see-also"></a>Voir aussi  
 [Mage.exe (outil Manifest Generation and Editing)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)   
 [Procédure pas à pas : déploiement manuel d’une application ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks > élément](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce et Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prérequis pour le déploiement d’applications](../deployment/application-deployment-prerequisites.md)