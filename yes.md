```json
{
  "project": {
    "name": "VibeSpecs",
    "domain": "vibespecs.app",
    "tagline": "Stop coding on vibes. Start coding with specs.",
    "status": "Active Development",
    "lastUpdated": "2025-10-03",
    "owner": "Josh Malone"
  },
  "productPositioning": {
    "audience": "VibeCoders — builders who use AI to create apps but struggle to turn ideas into working software",
    "targetUsers": [
      "non-technical founders",
      "designers",
      "PMs",
      "developers"
    ],
    "coreValue": "Convert messy, vibe-based prompts into precise, platform-agnostic JSON specs",
    "differentiator": "Multi-LLM peer review system with strict guardrails to prevent scope drift"
  },
  "problemStatement": {
    "description": "Developers struggle to communicate software requirements effectively to AI coding assistants",
    "painPoints": [
      "Inconsistent results",
      "Missing requirements",
      "Poorly structured code",
      "Time wasted on back-and-forth clarifications"
    ]
  },
  "solution": {
    "overview": "Three-stage refinement pipeline converting natural language into production-ready JSON specifications",
    "stages": {
      "stage1": {
        "name": "Prompt Optimization",
        "type": "Multimodal",
        "model": "Google Gemini 2.5 Pro",
        "input": [
          "Natural language prompt",
          "Optional images/screenshots/files"
        ],
        "output": "Initial structured JSON specification",
        "reasoning": [
          "Native multimodal capabilities",
          "Superior vision understanding for UI mockups",
          "Long context window (1M+ tokens)",
          "Cost-effective for multimodal processing",
          "Fast response times"
        ]
      },
      "stage2": {
        "name": "Multi-LLM Peer Review",
        "type": "4-Pass System",
        "passes": [
          {
            "passNumber": 1,
            "model": "Claude Sonnet 4.5",
            "role": "First Review",
            "focus": [
              "Technical architecture",
              "Code structure",
              "TypeScript/modern web development best practices"
            ]
          },
          {
            "passNumber": 2,
            "model": "GPT-5-mini",
            "role": "Second Review",
            "focus": [
              "Completeness",
              "Edge cases",
              "User flows",
              "Accessibility"
            ]
          },
          {
            "passNumber": 3,
            "model": "Claude Sonnet 4.5",
            "role": "Third Review",
            "focus": [
              "Technical implementation details",
              "Consistency",
              "Quality refinement"
            ]
          },
          {
            "passNumber": 4,
            "model": "GPT-5-mini",
            "role": "Final Polish",
            "focus": [
              "Final quality check",
              "Validation against best practices",
              "Completeness verification"
            ]
          }
        ]
      },
      "stage3": {
        "name": "Output Delivery",
        "output": "Finalized JSON specification",
        "format": "Clean, validated JSON",
        "compatibility": [
          "Cursor",
          "Warp AI",
          "ChatGPT",
          "GitHub Copilot",
          "Claude"
        ]
      }
    }
  },
  "peerReviewSystem": {
    "systemPromptComponents": [
      "Role awareness (pass number, counterpart model)",
      "Ground truth reference (original JSON from Stage 1)",
      "Edit history transparency",
      "Strict guardrails",
      "Complementary expertise"
    ],
    "guardrails": {
      "prohibited": [
        "Inventing new features not in original prompt",
        "Hallucinating requirements",
        "Complete redesigns or scope changes"
      ],
      "allowed": [
        "Improvements backed by best practices",
        "Changes that genuinely enhance quality",
        "Focus on model strengths, defer to counterpart strengths"
      ]
    },
    "modelExpertise": {
      "claudeSonnet45": [
        "Architecture",
        "Code structure",
        "TypeScript patterns",
        "Testing strategies",
        "Type safety"
      ],
      "gpt5Mini": [
        "Completeness",
        "Edge cases",
        "User flows",
        "Accessibility",
        "Documentation"
      ]
    }
  },
  "userJourney": [
    {
      "step": 1,
      "name": "Sign Up / Sign In",
      "details": [
        "GitHub and Google OAuth via NextAuth",
        "Database session in Supabase Postgres",
        "Auto-created user profile"
      ]
    },
    {
      "step": 2,
      "name": "Dashboard Access",
      "details": [
        "Protected route requiring authentication",
        "Usage meter shows daily quota",
        "Access to refinement interface"
      ]
    },
    {
      "step": 3,
      "name": "Submit Prompt",
      "inputs": {
        "textInput": {
          "freeTrial": "650 word max",
          "standard": "1,500 word max",
          "proTeam": "2,000 word max"
        },
        "fileUpload": {
          "types": [
            "Screenshots",
            "Design mockups",
            "Code files",
            "Database diagrams",
            "Reference images"
          ],
          "limits": {
            "freeTrial": "1 file only",
            "standard": "3 files per refinement",
            "proTeam": "Unlimited files"
          }
        }
      }
    },
    {
      "step": 4,
      "name": "Refinement Process",
      "duration": "15-20 seconds total",
      "substeps": [
        "Gemini 2.5 Pro analyzes prompt + images (3-5 seconds)",
        "Multi-LLM peer review (4 passes, ~10-15 seconds total)"
      ],
      "ui": [
        "Progress indicator",
        "Real-time status updates"
      ]
    },
    {
      "step": 5,
      "name": "Results Display",
      "features": [
        "Formatted JSON code block",
        "Copy button",
        "Download option (future)",
        "Refine again option",
        "Auto quota increment"
      ]
    },
    {
      "step": 6,
      "name": "Usage & Billing",
      "features": [
        "Monthly quota tracking",
        "Quota resets on billing cycle",
        "Stripe subscription management",
        "30-day refinement history (paid tiers)",
        "Usage dashboard"
      ]
    }
  ],
  "technicalArchitecture": {
    "techStack": {
      "framework": "Next.js 15 (App Router) + TypeScript",
      "styling": "Tailwind CSS v4 (dark theme)",
      "database": "Supabase (PostgreSQL) via Prisma ORM",
      "authentication": "NextAuth.js with GitHub and Google providers",
      "payments": "Stripe (subscriptions + webhooks)",
      "aiProcessing": "Supabase Edge Functions (Deno runtime)",
      "deployment": "Vercel"
    },
    "databaseSchema": {
      "coreModels": [
        {
          "name": "User",
          "purpose": "Authentication, profile, relationships"
        },
        {
          "name": "Account",
          "purpose": "NextAuth OAuth accounts"
        },
        {
          "name": "Session",
          "purpose": "NextAuth sessions"
        },
        {
          "name": "QuotaUsage",
          "purpose": "Daily usage tracking per user"
        }
      ],
      "refinementModels": [
        {
          "name": "RefinementJob",
          "fields": [
            "id",
            "userId",
            "status",
            "input",
            "output",
            "error",
            "tokensPrompt",
            "tokensCompletion",
            "costCents",
            "startedAt",
            "finishedAt",
            "createdAt",
            "updatedAt"
          ],
          "statusEnum": [
            "pending",
            "running",
            "succeeded",
            "failed",
            "canceled"
          ]
        },
        {
          "name": "RefinementStep",
          "fields": [
            "id",
            "jobId",
            "stepNo",
            "model",
            "input",
            "output",
            "valid",
            "durationMs",
            "tokensPrompt",
            "tokensCompletion"
          ],
          "relationship": "Belongs to RefinementJob"
        }
      ]
    },
    "apiRoutes": [
      {
        "path": "/api/review",
        "method": "POST",
        "purpose": "Main refinement endpoint",
        "authentication": "Required",
        "quotaCheck": true,
        "process": [
          "Validates user session",
          "Validates prompt payload (8-1000 chars)",
          "Checks daily quota (429 if exceeded)",
          "Calls Supabase Edge Function (refinery)",
          "Creates RefinementJob and RefinementStep records",
          "Returns refined JSON result",
          "Increments quota counter"
        ]
      },
      {
        "path": "/api/user/quota",
        "methods": [
          "GET",
          "POST"
        ],
        "get": "Returns current usage summary (usage, limit, resetsAt)",
        "post": "Manual quota increment (admin/testing)"
      },
      {
        "path": "/api/stripe/checkout",
        "method": "POST",
        "purpose": "Creates Stripe checkout session",
        "authentication": "Required"
      },
      {
        "path": "/api/stripe/webhook",
        "method": "POST",
        "purpose": "Handles Stripe webhook events",
        "validation": "Webhook signature verification"
      }
    ],
    "edgeFunctions": {
      "refinery": {
        "location": "supabase/functions/refinery/index.ts",
        "runtime": "Deno",
        "purpose": "Orchestrates 5-step refinement pipeline",
        "currentStatus": "Mock implementation",
        "productionSteps": [
          {
            "step": 0,
            "name": "Optimization",
            "model": "gemini-2.5-pro",
            "action": "Send user prompt + images, receive initial JSON"
          },
          {
            "step": 1,
            "name": "First Review",
            "model": "claude-sonnet-4.5",
            "action": "Improve initial JSON with architecture focus"
          },
          {
            "step": 2,
            "name": "Second Review",
            "model": "gpt-5-mini",
            "action": "Enhance with completeness and edge case focus"
          },
          {
            "step": 3,
            "name": "Third Review",
            "model": "claude-sonnet-4.5",
            "action": "Refine technical implementation"
          },
          {
            "step": 4,
            "name": "Final Polish",
            "model": "gpt-5-mini",
            "action": "Final validation and optimization"
          }
        ],
        "errorHandling": [
          "Individual step failure tracking",
          "Job marked as failed on critical errors",
          "Partial results saved for debugging",
          "Retry logic for transient errors"
        ],
        "costTracking": [
          "Token usage per step",
          "Cost calculation based on model pricing",
          "Aggregated at job level"
        ]
      }
    }
  },
  "features": {
    "implemented": [
      "GitHub OAuth authentication",
      "Protected dashboard route",
      "Daily quota tracking and enforcement",
      "Stripe checkout integration",
      "Webhook handling for subscriptions",
      "Prisma database schema with refinement models",
      "Basic review form UI component",
      "Usage meter component",
      "Modern dark theme with Tailwind v4",
      "Animated landing page with gradients"
    ],
    "inProgress": [
      "Multimodal input (image/file uploads)",
      "Gemini 2.5 Pro optimizer implementation",
      "Multi-LLM peer review pipeline (Sonnet + GPT-5-mini)",
      "RefinementJob/RefinementStep tracking",
      "Cost and token usage analytics",
      "Real-time progress indicators"
    ],
    "planned": [
      "Refinement history view",
      "JSON validation and syntax highlighting",
      "Export options (JSON, Markdown, PDF)",
      "Saved prompts/templates library",
      "Team collaboration features",
      "Advanced analytics dashboard",
      "API access for power users",
      "Webhook notifications for job completion",
      "Custom model selection"
    ]
  },
  "pricingTiers": {
    "freeTrial": {
      "price": 0,
      "refinements": 1,
      "wordLimit": 650,
      "fileUploads": 1,
      "peerReview": true,
      "historyDays": 0,
      "purpose": "Zero-friction experience of multi-LLM refinement",
      "costPerUser": 0.06,
      "features": [
        "Full 5-step peer review",
        "Real-time progress indicator",
        "No credit card required"
      ]
    },
    "standard": {
      "price": 20,
      "currency": "USD",
      "period": "month",
      "refinements": 30,
      "wordLimit": 1500,
      "fileUploads": 3,
      "peerReview": true,
      "historyDays": 30,
      "support": "email",
      "cost": 2.10,
      "margin": "89%",
      "valuePerRefinement": 0.67,
      "target": "Individual developers, freelancers"
    },
    "pro": {
      "price": 40,
      "currency": "USD",
      "period": "month",
      "refinements": 75,
      "wordLimit": 2000,
      "fileUploads": "unlimited",
      "peerReview": true,
      "historyDays": 30,
      "support": "email",
      "cost": 6.00,
      "margin": "85%",
      "valuePerRefinement": 0.53,
      "savings": "21% cheaper than Standard",
      "target": "Active developers, power users, small agencies",
      "badge": "Most Popular"
    },
    "team": {
      "price": 120,
      "currency": "USD",
      "period": "month",
      "refinements": 250,
      "wordLimit": 2000,
      "fileUploads": "unlimited",
      "peerReview": true,
      "historyDays": 30,
      "support": "email",
      "collaboration": true,
      "cost": 20.00,
      "margin": "83%",
      "valuePerRefinement": 0.48,
      "savings": "28% cheaper than Standard",
      "target": "Development teams, agencies, companies",
      "features": [
        "Team collaboration workspace",
        "Shared refinements"
      ]
    },
    "enterprise": {
      "price": "custom",
      "target": "Large organizations with custom needs",
      "features": [
        "Custom refinement volumes",
        "On-premise deployment options",
        "SLA guarantees",
        "Dedicated support",
        "Custom integrations",
        "Negotiated pricing"
      ]
    }
  },
  "successMetrics": {
    "product": [
      "Refinement Quality Score (user ratings)",
      "Time to Refinement (average processing time)",
      "Success Rate (% of jobs completing without errors)",
      "Model Agreement Rate (minimal changes between reviews)"
    ],
    "business": [
      "Daily Active Users (DAU)",
      "Monthly Recurring Revenue (MRR)",
      "Conversion Rate (Free to Paid)",
      "Churn Rate",
      "Average Refinements per User",
      "Cost per Refinement (API costs)"
    ],
    "satisfaction": [
      "NPS Score",
      "Feature Requests",
      "Bug Reports",
      "Support Tickets"
    ]
  },
  "competitiveAdvantages": [
    "Only platform using competitive peer review",
    "Multimodal input (images/screenshots)",
    "Platform agnostic JSON output",
    "Transparent refinement process",
    "Cost effective multi-model approach",
    "Developer-focused design"
  ],
  "environmentVariables": {
    "auth": [
      "NEXTAUTH_SECRET",
      "NEXTAUTH_URL",
      "GITHUB_ID",
      "GITHUB_SECRET",
      "GOOGLE_CLIENT_ID",
      "GOOGLE_CLIENT_SECRET"
    ],
    "database": [
      "DATABASE_URL",
      "DIRECT_URL"
    ],
    "stripe": [
      "STRIPE_SECRET_KEY",
      "STRIPE_WEBHOOK_SECRET",
      "STRIPE_PRICE_PRO_ID"
    ],
    "refinery": [
      "REFINERY_URL",
      "REFINERY_SERVICE_ROLE_KEY"
    ],
    "quotas": [
      "QUOTA_DAILY_LIMIT"
    ],
    "aiApis": [
      "GEMINI_API_KEY",
      "ANTHROPIC_API_KEY",
      "OPENAI_API_KEY"
    ]
  },
  "externalServices": [
    "Supabase (PostgreSQL + Edge Functions)",
    "Stripe (Payment processing)",
    "GitHub (OAuth provider)",
    "Vercel (Hosting)",
    "Google AI (Gemini 2.5 Pro)",
    "Anthropic (Claude Sonnet 4.5)",
    "OpenAI (GPT-5-mini)"
  ],
  "performanceRequirements": {
    "refinementCompletion": "< 30 seconds",
    "dashboardLoad": "< 2 seconds",
    "apiResponse": "< 500ms",
    "uptime": "99.9% (paid tiers)"
  },
  "developmentWorkflow": {
    "branches": {
      "main": "Production-ready code",
      "feature": "New feature development",
      "specKitPoc": "Testing Spec Kit integration"
    },
    "testing": {
      "unit": "Vitest for utilities and helpers",
      "integration": "API route testing",
      "e2e": "Playwright for critical user flows",
      "qa": "Manual refinement quality validation"
    },
    "deployment": {
      "platform": "Vercel",
      "environments": [
        "Production",
        "Preview",
        "Development"
      ],
      "cicd": "GitHub Actions (future)",
      "migrations": "Prisma migrate"
    }
  },
  "futureConsiderations": {
    "scalability": [
      "Queue system for refinement jobs (BullMQ/Inngest)",
      "Caching layer for common prompts (Redis)",
      "Edge caching for static assets",
      "Database read replicas for analytics"
    ],
    "aiModelUpdates": [
      "Version tracking for models",
      "A/B testing new model combinations",
      "User feedback loop to improve system prompts",
      "Fine-tuned models for specific domains"
    ],
    "featureExpansions": [
      "Code generation integration (one-click deploy)",
      "Browser extension for quick access",
      "IDE plugins (VS Code, Cursor)",
      "Slack/Discord bot integration",
      "API marketplace for third-party integrations"
    ]
  }
}

```
