# Conflit russo-ukrainien - Synthèse opérationnelle

| Version |
|---|
| 2022-03-01 |

| Auteurs |
|---|
| Cédric BLANDAMOUR |
| Capucine DE NOMAZY |
| Jérémy ROLLAND |



## Recommandations générales

### Recommandations générales prioritaires

* Réduire le risque d’usurpation de compte en renforçant l’authentification, en priorité sur les accès VPN et autres services exposés et des comptes administrateurs qui ont accès à l’ensemble des ressources critiques du SI
  * Mettre en place une authentification forte (avec deux facteurs d’authentification) sur tous les accès à distance au réseau de l'organisation et les accès privilégiés ou administratifs.
  * Vérifier que la politique de mot de passe inclut complexité, blocage en cas de brute force, revue des comptes et désactivation des comptes inutilisés.
  * Activer des filtres anti-spam puissants pour empêcher les courriels de phishing d'atteindre les utilisateurs finaux.

* Accroître le système de supervision de sécurité des événements journalisés
  * A minima, valider la génération des logs sur les points pertinents et centraliser les journaux des points les plus sensibles : les points d’entrée VPN, les bastions d’administration, les contrôleurs de domaine, les hyperviseurs.
  * Investiguer les anomalies susceptibles d’être ignorées en temps normal. Plus particulièrement, en environnement Active Directory, les connexions anormales sur les contrôleurs de domaine doivent être inspectées, ainsi que les alertes dans les consoles d’antivirus et EDR.
  * Si possible, déployer les outils de monitoring (Sysmon, EDR, XDR)
  * En cas de relations professionnelles avec des organisations opérant dans les zones concernées par le conflit : surveiller et inspecter en provenance de ces organisations ; examiner attentivement les contrôles d'accès à ce trafic.

* Sauvegarder hors-ligne les données et les applications critiques 
  * Sauvegardes régulières des actifs critiques de l’entreprise (serveurs de fichiers, d’infrastructures et d’applications métier…). La fréquence est à adapter en fonction de l’entité et la criticité des éléments sauvegardés.
  * Avoir au moins un niveau de sauvegardes déconnecté du SI, dont l’index des cassettes sur bandes.
  * Tester les procédures de sauvegarde des données critiques pour s’assurer de la rapidité et efficacité de leur restauration.

* Sanctuariser les activités et services critiques pour l’entité
  * Avoir à disposition un inventaire des services numériques associés aux activités métiers, listés par sensibilité.
  * Identifier les dépendances vis-à-vis de prestataires.
  * S'assurer que les logiciels sont à jour, en donnant la priorité aux mises à jour qui traitent des vulnérabilités connues. 

* S’assurer de l’existence d’un dispositif de gestion de crise adapté à une cyberattaque
  * Désigner une équipe de réponse à la crise et s’assurer de la maîtrise de chacun de ses rôles/responsabilités au sein de l'organisation, notamment en matière de technologie, de communication, de droit et de continuité des activités.
  * Avoir à disposition un plan de continuité d’activité et un plan de fonctionnement dégradé en cas d’indisponibilité des systèmes, des applications métiers et des fonctions supports (dont moyens de communication tels que téléphonie ou messagerie).
  * Définir des points de contact d’urgence, y compris chez les prestataires de services numériques. 
  * S’assurer d’avoir l’ensemble des informations utiles en version papier ou accessible hors réseau.

* Préparer une procédure « Bouton rouge » 
  * Préparer des procédures d’urgences permettant d’isoler des sections du système d’information qui seraient à risques (zones réseau contenant les équipements / bureau des zones concernées par le conflit. Actuellement Ukraine ou Russie).

* Suivre les alertes et avis de sécurité émis par des éditeurs de confiance
  * Liste de sources à suivre ci-dessous.


(Plus de détails dans le [rapport de l’ANSSI](https://www.ssi.gouv.fr/uploads/2022/02/20220226_mesures-cyber-preventives-prioritaires.pdf), le [rapport CISA](https://www.cisa.gov/sites/default/files/publications/cisa_insight_mitigating_foreign_influence_508.pdf) et le [rapport de presse de NCSC](https://www.ncsc.gov.uk/news/uk-organisations-encouraged-to-take-action-around-ukraine-situation))


### Recommandations spécifiques aux logiciels malveillants identifiés dans le contexte des tensions internationales février-mars 2022

Vous trouverez ci-joint un document listant les indicateurs de compromission connus à ce jour, liés au contexte. Assurez-vous qu’aucun indicateur ne se trouve sur votre réseau. 
Voici des recommandations spécifiques quant aux malwares et vulnérabilités identifiés : 


**Botnets :**
* Cyclops Blink : un botnet sophistiqué parrainé par des instances étatiques, susceptible d'avoir infecté un nombre limité d'appliances firewall WatchGuard. Celui-ci serait lié à l’APT Sandworm Team, comme indiqué dans [le rapport d’analyse du malware de NCSC](https://www.ncsc.gov.uk/files/Cyclops-Blink-Malware-Analysis-Report.pdf).
  * Remédiation : Suivre le plan détaillé de WatchGuard en 4 étapes : https://detection.watchguard.com/
  * Remédiation : Bloquer les IPs et noms de domaine présents dans le document d’indicateur de compromission ci-joint.

* Katana : un botnet utilisé pour réaliser des attaques DDOS.
  * Remédiation : Etablir un plan d’opération contre le DDOS. Un document a été publié par [l’ANSSI](https://www.ssi.gouv.fr/uploads/2015/03/NP_Guide_DDoS.pdf) en 2015. 
  * Remédiation : Bloquer les IPs et noms de domaine présents dans le document d’indicateur de compromission ci-joint.


**Destructive Malware :**
* WhisperGate : Le 15 janvier 2022, le Microsoft Threat Intelligence Center (MSTIC) a révélé que ce logiciel malveillant était utilisé pour cibler des organisations en Ukraine. Selon Microsoft, WhisperGate est destiné à être destructeur et est conçu pour rendre les appareils ciblés inopérants.

* HermeticWiper. Le 23 février 2022, plusieurs chercheurs en cybersécurité ont révélé qu'un logiciel malveillant connu sous le nom de HermeticWiper était utilisé contre des organisations en Ukraine. Selon SentinelLabs, le logiciel malveillant cible les appareils Windows, en manipulant l'enregistrement de démarrage principal, ce qui entraîne un échec de démarrage ultérieur.


**Vulnérabilités exploitées et mises à jour nécessaires :**
* CVE-2021-32648 Vulnerability est une vulnérabilité dans la plateforme de système de gestion de contenu (CMS) OctoberCMS, qui serait à l'origine des attaques contre les sites Web du gouvernement ukrainien. Elle permet à un attaquant d'accéder à n'importe quel compte par le biais d'une demande de réinitialisation du mot de passe du compte spécialement conçue.
  * Les organisations utilisant OctoberCMS avant la version 472 et la version 1.1.5 sont encouragées à mettre à jour la dernière version.

* Microsoft SQL Server vulnerability (CVE-2021-1636) : Les attaquants semblent avoir exploité une vulnérabilité connue dans Microsoft SQL Server afin de compromettre au moins une des organisations ciblées, en utilisant la commande "whoami". 
  * Les organisations sont encouragées à suivre le communiqué de Microsoft et à mettre à jour la dernière version.


## Sources à suivre

### Sources d’alertes généralistes :
* https://www.cert.ssi.gouv.fr/
* https://www.enisa.europa.eu/
* https://www.cisa.gov/stopransomware


### Sources de recommandations 
* https://www.ncsc.gov.uk/news/uk-organisations-encouraged-to-take-action-around-ukraine-situation
* https://www.cisa.gov/uscert/sites/default/files/publications/AA22-057A_Destructive_Malware_Targeting_Organizations_in_Ukraine.pdf
* https://www.ssi.gouv.fr/uploads/2022/02/20220226_mesures-cyber-preventives-prioritaires.pdf
* https://www.watchguard.com/fr/wgrd-news/blog/mesures-de-remediation-et-de-detection-du-botnet-cyclops-blink-parraine-par-des
* https://unit42.paloaltonetworks.com/ukraine-cyber-conflict-cve-2021-32648-whispergate/


### Sources Indicateurs de Compromission : 
* https://otx.alienvault.com/
* https://www.threatminer.org/
* https://www.virustotal.com/gui/home/upload
* https://www.microsoft.com/security/blog/2022/01/15/destructive-malware-targeting-ukrainian-organizations/
* https://blog.talosintelligence.com/2022/01/ukraine-campaign-delivers-defacement.html
* https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/ukraine-wiper-malware-russia
* https://unit42.paloaltonetworks.com/preparing-for-cyber-impact-russia-ukraine-crisis/#indicators-of-compromise
* https://twitter.com/ESETresearch/status/1496581916367151115?s
* https://www.sentinelone.com/labs/hermetic-wiper-ukraine-under-attack/
* https://www.ncsc.gov.uk/files/Cyclops-Blink-Malware-Analysis-Report.pdf
* https://www.cadosecurity.com/technical-analysis-of-the-ddos-attacks-against-ukrainian-websites/
* https://www.reddit.com/r/crowdstrike/comments/t0vhe6/20220225_cool_query_friday_situational_awareness/?utm_source=share&utm_medium=ios_app&utm_name=iossmf
* https://www.nioguard.com/2022/01/analysis-of-whispergate.html
* https://socradar.io/what-you-need-to-know-about-russian-cyber-escalation-in-ukraine/#IoCs-of-HermeticWiper


## Annexes

* [Les mesures d’hygiène informatique essentielles](https://www.ssi.gouv.fr/actualite/le-nouveau-guide-dhygiene-informatique-renforcer-la-securite-de-son-systeme-dinformation-en-42-mesures/#:~:text=Paru%20en%20janvier%202013%20dans%20sa%20premi%C3%A8re%20version%2C,qui%20y%20sont%20%C3%A9dict%C3%A9es%20avaient%20%C3%A9t%C3%A9%20appliqu%C3%A9es%20)  
* Les recommandations des guides de gestion de crise de l’ANSSI :
  * [« Crise d’origine cyber, les clés d’une gestion opérationnelle et stratégique »](https://www.ssi.gouv.fr/guide/crise-dorigine-cyber-les-cles-dune-gestion-operationnelle-et-strategique/). 
  * [« Anticiper et gérer sa communication de crise cyber »](https://www.ssi.gouv.fr/guide/anticiper-et-gerer-sa-communication-de-crise-cyber/).  
