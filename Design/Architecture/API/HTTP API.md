POST /account
Request: {
	"handle": string,
	"email": string,
	"password": string
}
Response: {
	"success": boolean,
	"error": string?
}


POST /account/verify?code={emailCode}
Request: Empty
Response: {
	"success": boolean,
	"error": string?
}


POST /account/verify/resend
Request: Empty
Response: {
	"success": boolean,
	"error": string?
}


PUT /account
Request: Auth header + multipart form data {
	thumbnail?: binary,
	banner?: binary,
	updates: {
		"displayName": string?,
		"bio": string?,
		"status": string?,
	}
}
Response: {
	"success": boolean,
	"error": string?
}


PATCH /account/handle 
Request: Auth header + {
	"handle": string,
}
Response: {
	"success": boolean,
	"error": string?
}


PATCH /account/email 
Request: Auth header + {
	"email": string,
}
Response: {
	"success": boolean,
	"error": string?
}


PATCH /account/password 
Request: Auth header + {
	"password": string,
}
Response: {
	"success": boolean,
	"error": string?
}


GET /account/friend-requests
Request: Auth header only
Response: [
	{
		"userId": guid,
		"handle": string,
		"displayName": string,
		"thumbnailUrl": string,
		"bannerUrl": string,
		"bio": string,
		"status": string,
		"mutualFriends": string[],
		"blocked": boolean
	}
]


GET /account/friends
Request: Auth header only
Response: [
	{
		"userId": guid,
		"handle": string,
		"displayName": string,
		"thumbnailUrl": string,
		"bannerUrl": string,
		"bio": string,
		"status": string,
		"mutualFriends": string[],
		"blocked": boolean
	}
]


GET /account/notifications
Request: Auth header only
Response: [
	{
		"senderType": string
		"senderId": guid
		"title": string
		"description": string
		"attachmentUrl": string?
	}
]


DELETE /account
Request: Auth header + {
	"username": string,
	"password": string
}
Response: {
	"success": boolean,
	"error": string?
}


POST /auth/login
Request: {
	"username": string,
	"password": string,
	"deviceInfo": string
}
Response: {
	"success": boolean,
	"error": string?,
	"authToken": string,
	"sessionId": string
}


GET /auth/sessions
Request: Auth header only
Response  [
	{
		"sessionId": guid,
		"createdAt": datetime,
		"lastUsedAt": datetime,
		"deviceInfo": string
	}
]


DELETE /auth/sessions/{sessionId}
Request: Auth header only
Response {
	"success": boolean,
	"error": string?
}


DELETE /auth/sessions
Request: Auth header only
Response {
	"success": boolean,
	"error": string?
}


GET /auth/game-token
Request: Auth header only
Response: {
	"token": string
}


POST /auth/game-token
Request: Auth header only
Response: {
	"token": string
}


GET /auth/join-token
Request: Auth header only
Response: {
	"token": string,
	"expiresAt": datetime
}


POST /auth/join-token
Request: {
	"username": string,
	"token": string
}
Response: {
	"valid": boolean
}


GET /user/{userId}
Request: Auth header only
Response: {
	"handle": string,
	"displayName": string,
	"thumbnailUrl": string,
	"bannerUrl": string,
	"bio": string,
	"status": string,
	"createdAt": datetime,
	"mutualFriends": string[],
	"blocked": boolean
}


GET /users
Request: Auth header + {
	"userIds" string[]
}
Response: [
	{
		"handle": string,
		"displayName": string,
		"thumbnailUrl": string,
		"bannerUrl": string,
		"bio": string,
		"status": string,
		"createdAt": datetime,
		"mutualFriends": string[],
		"blocked": boolean
	}
]


POST /user/{userId}/friend
Request: Auth header only
Response {
	"accepted": boolean,
}


DELETE /user/{userId}/friend
Request: Auth header only
Response {
	"success": boolean,
	"error": string?
}


POST /user/{userId}/block
Request: Auth header only
Response {
	"success": boolean,
	"error": string?
}


GET /search?type={ user | avatar | world | prop }&name={name}&page={page}&limit={limit}&sort={sorting?}&filter={tags?}
Request: Auth header only
Response {
	"items": [...],
	"hasMore": boolean
}


POST /content
Request: Auth header only
Response {
	"contentId": guid,
}


PUT /content/{contentId}
Request: Auth header + multipart form data {
	file?: binary,
	metadata: {
		"name": string?,
		"description": string?,
		"contentWarningTags": string[]?,
		"thumbnailUrl": string?,
		"contentType": string?
	}
}
Response {
	"success": boolean,
	"error": string?
}


GET /content
Request: Auth header only
Response [
	{
		"id": guid,
		"name": string,
		"description": string,
		"ownerId": string,
		"isPublic": boolean,
		"createdAt": datetime,
		"updatedAt": datetime,
		"contentWarningTags": string[],
		"thumbnailUrl": string?,
		"contentType": string,
		"sharedWithUserIds": string[]
	}
]


GET /content/{contentId}
Request: Auth header only
Response {
	"id": guid,
	"name": string,
	"description": string,
	"ownerId": string,
	"isPublic": boolean,
	"createdAt": datetime,
	"updatedAt": datetime,
	"contentWarningTags": string[],
	"thumbnailUrl": string?,
	"contentType": string,
	"sharedWithUserIds": string[]? // Only included if requester is owner
}


PUT /content/{contentId}/share
Request: Auth header + {
	"userIds": string[]
}
Response {
	"success": boolean,
	"error": string?
}


DELETE /content/{contentId}
Request: Auth header only
Response {
	"success": boolean,
	"error": string?
}


GET /content/{contentId}/download
Request: Auth header only
Response: Binary file stream


GET /tickets
Request: Auth header only
Response [
	{
		"type": string,
		"title": string,
		"description": string,
		"status": string
	}
]


POST /ticket/publish
Request: Auth header + {
	"contentId": guid
}
Response {
	"success": boolean,
	"error": string?
}


POST /ticket/transfer-owner
Request: Auth header + {
	"contentId": guid
}
Response {
	"success": boolean,
	"error": string?
}


POST /ticket/report
Request: Auth header {
	"type": string (user | avatar | world | prop)
	"title": string
	"description": string
	"attachments": binary[]?
}
Response {
	"success": boolean,
	"error": string?
}