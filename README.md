### Hi there 👋

SELECT
  repository_language,
  COUNT(distinct(repository_url)) AS active_repos_by_url,
  YEAR(created_at) AS year,
  QUARTER(created_at) AS quarter,
FROM [githubarchive:github.timeline]
WHERE
    type="PushEvent"
GROUP BY
  repository_language,
  year,
  quarter
ORDER BY
  repository_language,
  year DESC,
  quarter DESC
