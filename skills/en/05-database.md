# Database & Data Engineering
> 37 skills | Design schemas, optimize queries, build pipelines, and run ML in production

## Database Design & Admin
| Skill | What it does | Level |
|-------|-------------|-------|
| `database` | Database development and operations | [CORE] |
| `database-design` | Schema design and normalization | [CORE] |
| `database-admin` | Cloud-native database administration | [SPEC] |
| `database-architect` | Design the data layer | [SPEC] |
| `database-optimizer` | Optimize database performance | [SPEC] |
| `database-migration` | Migrate across ORMs and databases | [SPEC] |
| `database-cloud-optimization-cost-optimize` | Reduce database cloud costs | [SPEC] |
| `database-migrations-sql-migrations` | Zero-downtime SQL migrations | [SPEC] |
| `database-migrations-migration-observability` | Monitor database migrations | [SPEC] |

## PostgreSQL
| Skill | What it does | Level |
|-------|-------------|-------|
| `postgresql` | Design PostgreSQL schemas | [CORE] |
| `postgresql-optimization` | Tune PostgreSQL queries | [SPEC] |
| `postgres-best-practices` | PostgreSQL optimization best practices | [SPEC] |
| `neon-postgres` | Serverless Postgres with Neon | [SPEC] |
| `using-neon` | Best practices for using Neon | [SPEC] |
| `claimable-postgres` | Provision temporary Postgres instances | [SPEC] |

## SQL & NoSQL
| Skill | What it does | Level |
|-------|-------------|-------|
| `sql-pro` | Modern cloud-native SQL | [CORE] |
| `sql-optimization-patterns` | Optimize SQL query performance | [SPEC] |
| `nosql-expert` | Work with Cassandra, MongoDB, and DynamoDB | [SPEC] |
| `cc-skill-clickhouse-io` | Analytics with ClickHouse | [SPEC] |

## Data Engineering
| Skill | What it does | Level |
|-------|-------------|-------|
| `data-engineer` | Build data pipelines and warehouses | [CORE] |
| `data-engineering-data-pipeline` | Design pipeline architecture | [SPEC] |
| `data-engineering-data-driven-feature` | Build data-driven features | [SPEC] |
| `data-quality-frameworks` | Data quality with Great Expectations | [SPEC] |
| `data-scientist` | Advanced analytics and ML | [SPEC] |
| `data-storytelling` | Tell stories through data visualization | [SPEC] |
| `dbt-transformation-patterns` | Transform data with dbt | [SPEC] |
| `spark-optimization` | Optimize Apache Spark jobs | [SPEC] |
| `airflow-dag-patterns` | Design Apache Airflow DAGs | [SPEC] |

## ML & Data Science
| Skill | What it does | Level |
|-------|-------------|-------|
| `ml-engineer` | Build production ML systems | [SPEC] |
| `mlops-engineer` | Run ML pipelines and tracking | [SPEC] |
| `ml-pipeline-workflow` | End-to-end MLOps workflow | [SPEC] |
| `machine-learning-ops-ml-pipeline` | Design ML pipeline architecture | [SPEC] |
| `computer-vision-expert` | Object detection and segmentation with YOLO | [SPEC] |

---

## Enriched Skills

### `firebase`
**What you need:** Sets up a complete backend for your app using Google Firebase, giving you user login, a real-time database, file storage, cloud functions, and web hosting -- all without managing your own servers.
**Level:** Beginner
**Tags:** #firebase #backend #auth #database #storage #hosting #serverless
**When to use:**
- You want a backend for your app without setting up and managing servers
- You need user authentication, a database, and file storage that all work together out of the box
- You are building a prototype or MVP and want to move fast with a proven platform
**Combine with:** `firebase` > `clerk-auth` > `react-nextjs-development` > `mobile-developer`
**Example prompt:** > /firebase Set up a Firebase backend for a task management app with Google login, Firestore database for tasks, and Cloud Functions that send reminder emails
**Don't use when:** You need a relational SQL database with complex queries and joins -- use `postgresql` or `supabase-automation` instead
