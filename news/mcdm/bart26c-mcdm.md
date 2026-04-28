---
title: 'Beitrag „Multi-Objective Optimization with Desirability and Morris-Mitchell Criterion" für MCDM 2026 angenommen'
date: "2026-04-28"
---

# Beitrag „Multi-Objective Optimization with Desirability and Morris-Mitchell Criterion" für MCDM 2026 angenommen

![Pareto-Front aus der Verdichter-Fallstudie: ursprüngliche Datenpunkte, durch das Surrogatmodell prädizierte Front und ausgewählter Bestpunkt.](../../figures/news/bart26c/pareto-front.png){fig-alt="Pareto-Front zweier Zielgrößen z1 und z8 aus der Verdichter-Fallstudie mit Originaldaten, prädizierter Front und Bestpunkt"}

`28. April 2026`

Das Programmkomitee der [MCDM 2026](https://mcdm2026.uni-wuppertal.de/en/welcome/) hat den Beitrag *Multi-Objective Optimization with Desirability and Morris-Mitchell Criterion* zur Präsentation angenommen. Autorinnen und Autoren sind [Prof. Dr. Thomas Bartz-Beielstein](https://www.th-koeln.de/personen/thomas.bartz-beielstein/) (TH Köln, THK-AI Forschungscluster), Eva Bartz und Alexander Hinterleitner (Bartz & Bartz GmbH, Gummersbach) sowie Christoph Leitenmeier und Ihab Abd El Hussein (Everllence SE, Engineering Turbocharger, Augsburg).

## Hintergrund

Die Arbeit ist aus einer Kooperation zwischen dem THK-AI Forschungscluster der TH Köln, der Bartz & Bartz GmbH und der [Everllence SE](https://www.everllence.com/en) entstanden. Everllence ist der neue Name der bisherigen MAN Energy Solutions mit Hauptsitz in Augsburg; das Unternehmen entwickelt Antriebs-, Dekarbonisierungs- und Effizienzlösungen für Schifffahrt, Energiewirtschaft und Industrie und beschäftigt rund 16.200 Mitarbeitende weltweit. Innerhalb der Geschäftsbereiche bündelt die Sparte *Engineering Turbocharger* in Augsburg die Entwicklung von Großturboladern für Marine-, Energie- und Industrieanwendungen. Anlass für die Studie ist eine industrielle Anwendung aus genau diesem Bereich der Verdichterentwicklung, bei der bereits vorhandene Versuchsdaten weitergenutzt werden müssen, ohne neue Experimente von Grund auf neu planen zu können.

[![Logo der MCDM 2026 in Wuppertal.](../../figures/news/bart26c/mcdm-2026-logo.jpg){fig-alt="Logo der MCDM-2026-Konferenz in Wuppertal mit Schwebebahn-Motiv" width=240}](https://mcdm2026.uni-wuppertal.de/en/welcome/)

Die [MCDM 2026](https://mcdm2026.uni-wuppertal.de/en/welcome/) ist die *28th International Conference on Multiple Criteria Decision Making* und findet vom 25. bis 29. Mai 2026 an der Bergischen Universität Wuppertal statt. Ausgerichtet wird sie von der Optimization Group der Universität Wuppertal unter dem Vorsitz von Kathrin Klamroth und Michael Stiglmayr. Unter dem Leitmotiv *Better Decisions for a Better Tomorrow* versammelt die Konferenz Forschung zu mehrkriterieller Entscheidungsunterstützung, multikriterieller Optimierung und zugehöriger Software – mit explizitem Bezug zu sozialen, ökologischen und ökonomischen Wirkungen.

## Fragestellung

In industriellen Versuchsplänen sind die Datenpunkte häufig ungleichmäßig im Eingangsraum verteilt; sie erfüllen die Anforderungen klassischer raumfüllender Designs nur näherungsweise. Damit wird die zugrunde liegende Stichprobe nicht repräsentativ für den gesamten Parameterraum, was die Qualität von Surrogatmodellen und nachgelagerten Optimierungsentscheidungen beeinträchtigt. Die zentrale Frage des Beitrags lautet daher, wie sich bestehende Designs nachträglich verbessern lassen, ohne die Verfolgung der eigentlichen Leistungsziele aus dem Blick zu verlieren. Dabei muss zugleich geklärt werden, wo die Aussagekraft des Morris-Mitchell-Kriteriums an ihre Grenzen stößt.

## Vorgehen

Der Beitrag analysiert Varianten des Morris-Mitchell-Kriteriums potentialtheoretisch und arbeitet Monotonieeigenschaften und Grenzen heraus. Auf dieser Grundlage entsteht ein multikriterielles Optimierungsverfahren, das Desirability-Funktionen nutzt, um Vorhersagen eines Surrogatmodells und raumfüllende Verbesserungen zu einem gemeinsamen Bewertungsmaß zu verschmelzen. Die Implementierung stützt sich auf die quelloffenen Python-Pakete [`spotdesirability`](https://sequential-parameter-optimization.github.io/spotdesirability/) und [`spotoptim`](https://sequential-parameter-optimization.github.io/spotoptim/docs/index.html). Ergänzt wird der Ansatz durch neuartige Infill-Point-Diagnostiken, die die sequenzielle Wahl neuer Designpunkte visuell nachvollziehbar machen.

![Beispiel eines durch das Morris-Mitchell-Kriterium bewerteten Designs (Φ₂ = 17,11) im zweidimensionalen Schnitt.](../../figures/news/bart26c/mm-design.png){fig-alt="Punktwolke eines zweidimensionalen Designs mit Morris-Mitchell-Kennwert"}

## Ergebnisse

Die Methodik wird an einer Fallstudie aus der Verdichterentwicklung der Everllence SE demonstriert. Zwei industrierelevante Zielgrößen werden gemeinsam optimiert, während die räumliche Abdeckung des Designs gezielt verbessert wird. Das Verfahren bringt Performance-Optimierung und Designqualität in einer einheitlichen Bewertung zusammen und überträgt damit Erkenntnisse aus der Theorie raumfüllender Designs konsequent in die ingenieurwissenschaftliche Praxis. Die Infill-Point-Diagnostiken machen den Trade-off zwischen Exploration und Exploitation transparent und unterstützen die schrittweise Erweiterung bestehender Versuchsreihen.

Zitation: Bartz-Beielstein, T., Bartz, E., Hinterleitner, A., Leitenmeier, C., Abd El Hussein, I. (2026). *Multi-Objective Optimization with Desirability and Morris-Mitchell Criterion.* Beitrag angenommen bei MCDM 2026.
